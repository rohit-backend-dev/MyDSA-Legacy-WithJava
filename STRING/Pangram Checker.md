# 📝 Pangram Checker in Java

## 📌 Problem Statement

A **pangram** is a sentence that contains every letter of the English alphabet at least once.
Given a string `sentence` containing only lowercase English letters, return `true` if `sentence` is a pangram, or `false` otherwise.

**Example:**
Input:

```
"thequickbrownfoxjumpsoverthelazydog"
```

Output:

```
true
```

---

## ✅ Approach 1: Using Boolean Array

We track each letter `a-z` using a boolean array of size 26.

* Each index represents a letter (`0 → 'a'`, `1 → 'b'`, ... , `25 → 'z'`).
* When a letter appears, mark it as `true`.
* Keep a count of unique letters seen.
* If `count == 26`, return `true`.

### Code

```java
class Solution {
    public boolean checkIfPangram(String sentence) {
        boolean[] seen = new boolean[26];
        int count = 0;

        for (char ch : sentence.toCharArray()) {
            int idx = ch - 'a';
            if (!seen[idx]) {
                seen[idx] = true;
                if (++count == 26) return true;
            }
        }
        return false; 
    }
}
```

**Complexity:**

* Time → `O(n)`
* Space → `O(1)` (since 26 is constant)

---

## ✅ Approach 2: Using HashSet

We use a `HashSet` to automatically store **unique characters**.

* Insert each character into the set.
* If the size of the set reaches 26, return `true`.

### Code

```java
import java.util.HashSet;
import java.util.Set;

class Solution {
    public boolean checkIfPangram(String sentence) {
        Set<Character> set = new HashSet<>();

        for (char ch : sentence.toCharArray()) {
            set.add(ch);
            if (set.size() == 26) return true;
        }

        return false;
    }
}
```

**Complexity:**

* Time → `O(n)`
* Space → `O(26)` = `O(1)`

---

## 🔑 Key Takeaways

* Boolean array → Faster, memory-efficient.
* HashSet → Cleaner, easier to understand.
* Both are optimal with **O(n)** time.

---

⚡ For fun, we can also solve it in **one-liner Java Streams**:

```java
import java.util.stream.Collectors;

class Solution {
    public boolean checkIfPangram(String sentence) {
        return sentence.chars()
                .mapToObj(c -> (char) c)
                .collect(Collectors.toSet())
                .size() == 26;
    }
}
```

