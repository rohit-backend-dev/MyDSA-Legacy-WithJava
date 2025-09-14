## ✅ Code for First **Non-Repeating Character**

```java
class Solution {
    public char firstNonRepeatingChar(String s) {
        int[] freq = new int[26];
        int n = s.length();

        // Count frequency
        for (int i = 0; i < n; i++) {
            freq[s.charAt(i) - 'a']++;
        }

        // Find first char with frequency == 1
        for (int i = 0; i < n; i++) {
            if (freq[s.charAt(i) - 'a'] == 1) {
                return s.charAt(i);
            }
        }

        return '$'; // no non-repeating char
    }
}
```

**Example:**

* Input: `"leetcode"` → Output: `'l'`
* Input: `"aabb"` → Output: `'$'`

---

## ✅ Code for First **Unique Character (Index)**

```java
class Solution {
    public int firstUniqChar(String s) {
        int[] freq = new int[26];
        int n = s.length();

        // Count frequency
        for (int i = 0; i < n; i++) {
            freq[s.charAt(i) - 'a']++;
        }

        // Return index of first unique char
        for (int i = 0; i < n; i++) {
            if (freq[s.charAt(i) - 'a'] == 1) {
                return i;
            }
        }

        return -1; // no unique char
    }
}
```

**Example:**

* Input: `"leetcode"` → Output: `0` (since `'l'` is at index 0)
* Input: `"aabb"` → Output: `-1`

---

✨ So:

* **First non-repeating char** → return `'char'` (or `'$'`).
* **First unique char (LeetCode)** → return `index` (or `-1`).
