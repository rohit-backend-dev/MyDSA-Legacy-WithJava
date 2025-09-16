
```java
import java.util.HashSet;

/**
 * Solution class to remove duplicate characters from a string.
 * 
 * <p>This method returns a new string that contains only the first occurrence
 * of each character in the input string, preserving the original order.
 * 
 * <p>Example:
 * <pre>
 * Input:  "programming"
 * Output: "progamin"
 * </pre>
 * 
 * <p>Time Complexity: O(n), where n is the length of the string.
 * <br>Space Complexity: O(k), where k is the number of unique characters.
 */
class Solution {

    /**
     * Removes duplicate characters from the input string.
     *
     * @param s The input string from which to remove duplicate characters.
     * @return A new string containing only the first occurrence of each character.
     */
    String removeDuplicates(String s) {
        // HashSet to store characters we've already seen
        HashSet<Character> set = new HashSet<>();

        // StringBuilder to efficiently build the result string
        StringBuilder result = new StringBuilder();

        // Iterate through each character in the input string
        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i); // Get the current character

            // If the character hasn't been seen before, add it to the result
            if (!set.contains(ch)) {
                set.add(ch);        // Mark the character as seen
                result.append(ch);  // Append the character to the result
            }
            // If the character is already in the set, skip it (duplicate)
        }

        // Convert the StringBuilder to a string and return it
        return result.toString();
    }
}
```
