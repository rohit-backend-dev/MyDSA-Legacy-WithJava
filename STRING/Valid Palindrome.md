# 📘 125. Valid Palindrome — Solutions in Java

## 📝 Problem

A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

---

# If pre-built functions are not allowed

```
class Solution {
    public boolean isPalindrome(String s) {
        int left = 0;
        int right = s.length() - 1;

        while (left < right) {
            // Move left to next valid character
            while (left < right && !isAlphanumeric(s.charAt(left))) {
                left++;
            }
            // Move right to previous valid character
            while (left < right && !isAlphanumeric(s.charAt(right))) {
                right--;
            }

            if (left < right) {
                char cLeft = toLowerCase(s.charAt(left));
                char cRight = toLowerCase(s.charAt(right));

                if (cLeft != cRight) {
                    return false;
                }
                left++;
                right--;
            }
        }
        return true;
    }

    // Helper to check if character is alphanumeric
    private boolean isAlphanumeric(char c) {
        return (c >= 'a' && c <= 'z') || (c >= 'A' && c <= 'Z') || (c >= '0' && c <= '9');
    }

    // Helper to convert uppercase to lowercase manually
    private char toLowerCase(char c) {
        if (c >= 'A' && c <= 'Z') {
            return (char)(c - 'A' + 'a');
        }
        return c;
    }
}

```


## ✅ Solution 1 — Clean String + Two Pointers

### 💡 Idea

1. Convert string to lowercase.
2. Remove all non-alphanumeric characters.
3. Use two pointers (`left` and `right`) to check palindrome.

### 🔗 Code

```java
class Solution {
    public boolean isPalindrome(String s) {
        // Step 1: lowercase + remove non-alphanumeric
        s = s.toLowerCase().replaceAll("[^a-z0-9]", "");

        // Step 2: two-pointer palindrome check
        int left = 0, right = s.length() - 1;
        while (left < right) {
            if (s.charAt(left) != s.charAt(right)) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }
}
```

### ⏱️ Complexity

* **Time Complexity:** O(n)

  * Lowercasing → O(n)
  * Regex replace → O(n)
  * Two-pointer check → O(n)
  * Overall still **O(n)**.
* **Space Complexity:** O(n) (extra cleaned string).

---

## ✅ Solution 2 — Two Pointers (Skip Non-Alphanumeric)

### 💡 Idea

Instead of building a new string, skip invalid characters while checking from both ends.

### 🔗 Code

```java
class Solution {
    public boolean isPalindrome(String s) {
        int left = 0, right = s.length() - 1;

        while (left < right) {
            // Skip non-alphanumeric on left
            while (left < right && !Character.isLetterOrDigit(s.charAt(left))) {
                left++;
            }
            // Skip non-alphanumeric on right
            while (left < right && !Character.isLetterOrDigit(s.charAt(right))) {
                right--;
            }
            // Compare after skipping
            if (Character.toLowerCase(s.charAt(left)) != Character.toLowerCase(s.charAt(right))) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }
}
```

### ⏱️ Complexity

* **Time Complexity:** O(n) (each character visited at most once).
* **Space Complexity:** O(1) (no extra cleaned string).

---

## 📊 Comparison

| Approach                    | Time Complexity | Space Complexity | Notes                                      |
| --------------------------- | --------------- | ---------------- | ------------------------------------------ |
| Clean string + two pointers | O(n)            | O(n)             | Easier to implement, but uses extra space. |
| Two pointers (skip chars)   | O(n)            | O(1)             | More optimal, preferred in interviews.     |

---

👉 For **coding rounds**, the first approach is shorter.
👉 For **interviews & production**, the second approach is optimal.

---

# Note


### `s = s.toLowerCase()`

* Makes the string **case-insensitive** (so `A` and `a` are treated the same).
* Do this first so regex only needs `[a-z0-9]` (all letters are already lowercase).

---

### `.replaceAll("[^a-z0-9]", "")`

* Removes everything **not a letter or number**.
* `[^...]` = "NOT these characters".
* `a-z0-9` = allowed characters.
* `""` = delete them completely.

---

👉 In short:

* `toLowerCase()` → normalize letters.
* `replaceAll("[^a-z0-9]", "")` → keep only letters & numbers, delete the rest.
