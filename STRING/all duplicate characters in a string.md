 👍 Printing **all duplicate characters in a string**

## 🔹 Problem Statement

Given a string, print all characters that occur **more than once**, along with their frequency.

---

## 🔹 Example

Input:

```
"programming"
```

Output:

```
r : 2
g : 2
m : 2
```

---

## 🔹 Approach

1. Use a **HashMap\<Character, Integer>** to store frequencies.
2. Traverse the string → count occurrences.
3. Print only those characters whose count > 1.

---

## 🔹 Java Code

```java
import java.util.HashMap;
import java.util.Map;

public class DuplicateCharacters {
    public static void printDuplicates(String str) {
        // Frequency map
        Map<Character, Integer> freqMap = new HashMap<>();

        // Count frequency of each char
        for (char c : str.toCharArray()) {
            freqMap.put(c, freqMap.getOrDefault(c, 0) + 1);
        }

        // Print duplicates
        System.out.println("Duplicate characters are:");
        for (Map.Entry<Character, Integer> entry : freqMap.entrySet()) {
            if (entry.getValue() > 1) {
                System.out.println(entry.getKey() + " : " + entry.getValue());
            }
        }
    }

    public static void main(String[] args) {
        String str = "programming";
        printDuplicates(str);
    }
}
```

---

## 🔹 Output

```
Duplicate characters are:
r : 2
g : 2
m : 2
```

---

✅ **Time Complexity:** `O(n)` (single pass for counting, single pass for printing)
✅ **Space Complexity:** `O(k)` where `k` = number of unique characters
ant me to also give you a **LeetCode-style version** (returning list of duplicates instead of printing)?
