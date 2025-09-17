```
class Solution {
    public String largestOddNumber(String num) {
        
        int n = num.length();

        // traverse from right to left
        for (int i = n - 1; i >= 0; i--) {
            int digit = num.charAt(i) - '0'; // convert char to int
            if (digit % 2 != 0) { // check odd
                return num.substring(0, i + 1); // correct method name
            }
        }
        return "";
    }
}

```
