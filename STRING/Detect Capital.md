```
class Solution {
    public boolean detectCapitalUse(String word) {
        
        int n=word.length();
        if (n==0) return true;

        boolean firstUpper = isUpper(word.charAt(0));
        boolean allUpper = firstUpper;
        boolean allLower = !firstUpper;

                for (int i = 1; i < n; i++) {
            if (isUpper(word.charAt(i))) {
                allLower = false;
            } else {
                allUpper = false;
            }
        }

        return allUpper || allLower || (firstUpper && !allUpper && !allLower);
    }



        private boolean isUpper(char c){
            return c >= 'A' && c <= 'Z';
        }
    }

```
