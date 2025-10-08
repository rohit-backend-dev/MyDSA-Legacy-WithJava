```
class Solution {
    public int strStr(String haystack, String needle) {
        int m = haystack.length();
        int n = needle.length();
        
        // Edge case: empty needle
        if (n == 0) return 0;
        
        // Loop through haystack
        for (int i = 0; i <= m - n; i++) { // i <= m - n to avoid index out of bounds
            int j;
            for ( j = 0; j < n; j++) {
                if (haystack.charAt(i + j) != needle.charAt(j)) {
                    break; 
                }
            }
            if (j == n) return i;
        }
        
        return -1;
    }
}

```
