```
class Solution {
    public boolean detectCapitalUse(String word) {
        int n = word.length();
        if (n == 0) return true;

        // Case 1: all uppercase
        if (isAllUpper(word)) return true;

        // Case 2: all lowercase
        if (isAllLower(word)) return true;

        // Case 3: first letter uppercase, rest lowercase
        if (isUpper(word.charAt(0)) && isAllLower(word.substring(1))) return true;

        return false;
    }

    private boolean isUpper(char c) {
        return c >= 'A' && c <= 'Z';
    }

    private boolean isAllUpper(String s) {
        for (char c : s.toCharArray()) {
            if (!isUpper(c)) return false;
        }
        return true;
    }

    private boolean isAllLower(String s) {
        for (char c : s.toCharArray()) {
            if (isUpper(c)) return false;
        }
        return true;
    }
}

```
