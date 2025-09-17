```
class Solution {
    public boolean rotateString(String s, String goal) {
        int n = s.length();

        // Lengths must match
        if (n != goal.length()) return false;

        // Concatenate s with itself
        String doubled = s + s;

        // Instead of contains(), check substring of exact length
        for (int i = 0; i < n; i++) {
            String rotation = doubled.substring(i, i + n);
            if (rotation.equals(goal)) {
                return true;
            }
        }

        return false;
    }
}

```
