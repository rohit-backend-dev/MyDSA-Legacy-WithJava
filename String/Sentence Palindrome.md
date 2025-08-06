### ✅ **What is a Sentence Palindrome?**
A **sentence palindrome** is a sentence that reads the same **forward and backward** when:

* All **letters are treated case-insensitively** (i.e., upper/lowercase doesn't matter),
* All **non-alphanumeric characters** like spaces, punctuation, and symbols are **ignored**.

---

### ✅ **Example:**

```java
Input: "Too hot to hoot."
```

After cleaning:

* Remove punctuation and spaces → `"toohottohoot"`
* Convert to lowercase → `"toohottohoot"`
* Reversed string is also `"toohottohoot"` → ✅ Palindrome!

---

### ✅ Java Code: Improved Version

Here's a **better structured and clean version** of the Java code using the same two-pointer approach:

```java
public class Solution {

    // Function to check if a sentence is a palindrome
    public static boolean isSentencePalindrome(String s) {
        int left = 0, right = s.length() - 1;

        while (left < right) {

            // Move left pointer to next alphanumeric character
            while (left < right && !Character.isLetterOrDigit(s.charAt(left))) {
                left++;
            }

            // Move right pointer to previous alphanumeric character
            while (left < right && !Character.isLetterOrDigit(s.charAt(right))) {
                right--;
            }

            // Compare characters case-insensitively
            if (Character.toLowerCase(s.charAt(left)) != Character.toLowerCase(s.charAt(right))) {
                return false;
            }

            left++;
            right--;
        }

        return true; // All checks passed
    }

    public static void main(String[] args) {
        String sentence = "Too hot to hoot.";
        boolean result = isSentencePalindrome(sentence);
        System.out.println(result ? "true" : "false");
    }
}
```

---

### ✅ Output:

```
true
```

