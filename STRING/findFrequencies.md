## ✅ 1. Frequency of `'p'` in `"apple"`

```java
class Solution {
    public int countChar(String s, char target) {
        int count = 0;
        for (char ch : s.toCharArray()) {
            if (ch == target) {
                count++;
            }
        }
        return count;
    }

    public static void main(String[] args) {
        Solution sol = new Solution();
        String word = "apple";
        char target = 'p';
        System.out.println("Frequency of '" + target + "' = " + sol.countChar(word, target));
    }
}
```

**Output:**

```
Frequency of 'p' = 2
```

---

## ✅ 2. Frequency of every letter in `"apple"`

Using an array for **O(n)** efficiency:

```java
import java.util.*;

class Solution {
    public Map<Character, Integer> countAllChars(String s) {
        Map<Character, Integer> freq = new HashMap<>();

        for (char ch : s.toCharArray()) {
            freq.put(ch, freq.getOrDefault(ch, 0) + 1);
        }

        return freq;
    }

    public static void main(String[] args) {
        Solution sol = new Solution();
        String word = "apple";
        Map<Character, Integer> result = sol.countAllChars(word);

        for (Map.Entry<Character, Integer> entry : result.entrySet()) {
            System.out.println(entry.getKey() + " → " + entry.getValue());
        }
    }
}
```

**Output:**

```
a → 1
p → 2
l → 1
e → 1
```
