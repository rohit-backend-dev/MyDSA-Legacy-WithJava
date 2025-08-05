### ✅ Problem Explanation:

You are given a **sentence `s`**, and you need to determine whether it's a **palindrome** after:

1. **Converting all uppercase letters to lowercase**
2. **Removing all non-alphanumeric characters** (i.e., keep only a-z, A-Z, 0-9)

---

### 🔁 What is a Palindrome?

A string is a **palindrome** if it reads the **same forward and backward**.

### 💡 Examples:

#### Example 1:

* **Input**: `"Too hot to hoot."`
* **Processing**:

  * Convert to lowercase → `"too hot to hoot."`
  * Remove non-alphanumeric → `"toohottohoot"`
* **Result**: `"toohottohoot"` == `"toohottohoot"` → ✅ **Palindrome**

#### Example 2:

* **Input**: `"Abc 012..##  10cbA"`
* **Processing** → `"abc01210cba"` → ✅ **Palindrome**

#### Example 3:

* **Input**: `"ABC $. def01ASDF.."`
* **Processing** → `"abcdef01asdf"` → ❌ **Not a palindrome**

---

## 👨‍💻 Brute Force Solution:

### ✅ Steps:

1. Create a **new string** with only lowercase alphanumeric characters.
2. Reverse this cleaned string.
3. Compare cleaned and reversed strings.

### 💻 Java Code (Brute Force):

```java
public class PalindromeSentenceChecker {

    public static boolean isPalindromeBrute(String s) {
        StringBuilder cleaned = new StringBuilder();

        // Step 1: Clean the string
        for (char c : s.toCharArray()) {
            if (Character.isLetterOrDigit(c)) {
                cleaned.append(Character.toLowerCase(c));
            }
        }

        // Step 2: Reverse the cleaned string
        StringBuilder reversed = new StringBuilder(cleaned).reverse();

        // Step 3: Compare original cleaned with reversed
        return cleaned.toString().equals(reversed.toString());
    }

    public static void main(String[] args) {
        System.out.println(isPalindromeBrute("Too hot to hoot."));      // true
        System.out.println(isPalindromeBrute("Abc 012..##  10cbA"));    // true
        System.out.println(isPalindromeBrute("ABC $. def01ASDF.."));    // false
    }
}
```

### ⏱ Time Complexity:

* O(n) to clean the string
* O(n) to reverse and compare → **O(n)** total time
* O(n) space for cleaned and reversed string

---

## 🚀 Optimal Two-Pointer Solution:

### ✅ Idea:

* Use two pointers: `left` (start) and `right` (end)
* Move both pointers inward, skipping non-alphanumeric characters
* Compare characters (after converting to lowercase)
* If mismatch → return false
* If loop ends → it's a palindrome

### 💻 Java Code (Optimal):

```java
public class Solution {

    // Function to check if a given sentence is a palindrome
    static boolean isPalindromeOptimal(String s) {
        int i = 0, j = s.length() - 1;

        // Compare characters from both ends until they meet
        while (i < j) {

            // Skip non-alphanumeric character from the left side
            if (!Character.isLetterOrDigit(s.charAt(i))) {
                i++;
            }
            // Skip non-alphanumeric character from the right side
            else if (!Character.isLetterOrDigit(s.charAt(j))) {
                j--;
            }
            // If characters match (ignoring case), move both pointers
            else if (Character.toLowerCase(s.charAt(i)) 
                    == Character.toLowerCase(s.charAt(j))) {
                i++;
                j--;
            }
            // Characters don't match – not a palindrome
            else {
                return false;
            }
        }

        // All characters matched – it is a palindrome
        return true;
    }

    public static void main(String[] args) {
        String s = "Too hot to hoot.";
        System.out.println(isPalinSent(s) ? "true" : "false");
    }
}

```

### ⏱ Time Complexity:

* **O(n)** time
* **O(1)** space (no extra memory used)

---

## ✅ Final Thoughts:

| Approach    | Time | Space | Notes                          |
| ----------- | ---- | ----- | ------------------------------ |
| Brute Force | O(n) | O(n)  | Easy to implement, extra space |
| Two Pointer | O(n) | O(1)  | Best performance, in-place     |
