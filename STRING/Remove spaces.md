```
// User function Template for Java
class Solution {
    String modify(String s) {
        StringBuilder result = new StringBuilder();

        // iterate over each character
        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);

            // only add non-space characters
            if (ch != ' ') {
                result.append(ch);
            }
        }

        return result.toString();
    }
}

```
