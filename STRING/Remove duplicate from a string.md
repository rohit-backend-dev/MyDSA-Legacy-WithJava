```
import java.util.HashSet;

class Solution {
    String removeDuplicates(String s) {
        // Create a HashSet to store seen characters
        HashSet<Character> set = new HashSet<>();

        // Use a StringBuilder to efficiently build the result
        StringBuilder result = new StringBuilder();

        // Traverse each character in the input string
        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);

            // If the character is not in the set, it's the first occurrence
            if (!set.contains(ch)) {
                set.add(ch);           // Add character to the set
                result.append(ch);     // Append character to result
            }
            // If already in set, do nothing (skip duplicates)
        }

        // Return the final string with duplicates removed
        return result.toString();
    }
}

```
