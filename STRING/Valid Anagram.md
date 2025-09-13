## 📌 242. Valid Anagram

### 📌 Solution 1: Using HashMap

```java
import java.util.*;

class Solution {
    // ✅ HashMap based solution
    public static boolean areAnagrams(String s, String t) {
        if (s.length() != t.length()) return false;

        Map<Character, Integer> map = new HashMap<>();

        // Count and balance simultaneously
        for (int i = 0; i < s.length(); i++) {
            char sc = s.charAt(i);
            char tc = t.charAt(i);

            map.put(sc, map.getOrDefault(sc, 0) + 1);
            map.put(tc, map.getOrDefault(tc, 0) - 1);
        }

        // If any char has non-zero count → not an anagram
        for (int count : map.values()) {
            if (count != 0) return false;
        }
        return true;
    }
}
```

🔑 **Key Points**

* Works for any character set (letters, numbers, symbols).
* O(n) time, O(k) space (k = unique chars).

---

### 📌 Solution 2: Using Array 

```java
class SolutionArray {
    // ✅ Array frequency solution
    public static boolean areAnagrams(String s, String t) {
        if (s.length() != t.length()) return false;

        int[] freq = new int[26]; // only lowercase letters

        for (int i = 0; i < s.length(); i++) {
            freq[s.charAt(i) - 'a']++;
            freq[t.charAt(i) - 'a']--;
        }

        for (int count : freq) {
            if (count != 0) return false;
        }
        return true;
    }
}
```

🔑 **Key Points**

* Uses fixed-size array → **O(1) space**.
* O(n) time, faster than HashMap.
* Only valid if strings contain **lowercase English letters**.

---
