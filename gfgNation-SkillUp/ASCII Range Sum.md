## 🔸 Problem Statement Recap

Given a string `s` of lowercase English letters, find all characters whose **first and last occurrence are at different positions**. For each such character:

* Compute the **sum of ASCII values** of characters **strictly between** its first and last occurrence.
* Return the list of **non-zero** sums.
* **Order of sums doesn't matter.**

---

## 🧠 Intuition

We need to:

1. Track **first and last index** of each character.
2. For characters with **first index ≠ last index**, calculate sum of ASCII values **strictly between** these two indices.
3. Add the result to the answer list **only if the sum > 0**.

---

## 🧪 Example Walkthrough

### ✅ Example 1: `"abacab"`

```
Index:   1 2 3 4 5 6
String:  a b a c a b

Unique characters: a, b, c

'a':
  first = 1, last = 5
  characters between: b, a, c → ASCII: 98 + 97 + 99 = 294

'b':
  first = 2, last = 6
  characters between: a, c, a → ASCII: 97 + 99 + 97 = 293

'c':
  only one occurrence → skip
```

**Result:** \[294, 293]

---

### ✅ Example 2: `"acdac"`

```
Index:   1 2 3 4 5
String:  a c d a c

'a':
  first = 1, last = 4 → characters between: c, d → 99 + 100 = 199

'c':
  first = 2, last = 5 → characters between: d, a → 100 + 97 = 197

'd':
  only one occurrence → skip
```

**Result:** \[199, 197]

---

## 🐢 Brute Force Solution

### 🔍 Approach

* For each character from 'a' to 'z':

  * Scan string to find **first and last** position.
  * If positions differ, loop from `first+1` to `last-1`, add ASCII values.

### ✅ Time Complexity: `O(26 * N)` → simplified to `O(N)`

Where `N` is the length of the string.

---

### 📦 Java Code (Brute Force)

```java
import java.util.*;

public class ASCIIRangeSum {
    public static List<Integer> bruteForceASCII(String s) {
        List<Integer> result = new ArrayList<>();

        for (char ch = 'a'; ch <= 'z'; ch++) {
            int first = -1, last = -1;
            for (int i = 0; i < s.length(); i++) {
                if (s.charAt(i) == ch) {
                    if (first == -1) first = i;
                    last = i;
                }
            }

            if (first != -1 && last != -1 && first != last) {
                int sum = 0;
                for (int i = first + 1; i < last; i++) {
                    sum += s.charAt(i);
                }
                if (sum != 0) result.add(sum);
            }
        }

        return result;
    }

    public static void main(String[] args) {
        System.out.println(bruteForceASCII("abacab")); // [294, 293]
        System.out.println(bruteForceASCII("acdac"));  // [197, 199]
    }
}
```

---
## ⚡ Optimal Solution (Array-based for lowercase only)

### 🔍 **Example**

**Input:** `"abcaebd"`

**Step-by-step:**

* Character `'a'` occurs at indices 0 and 3 → characters in between: `'b'`, `'c'`
  ASCII sum = 98 (`'b'`) + 99 (`'c'`) = **197**

* Character `'b'` occurs at indices 1 and 6 → characters in between: `'c'`, `'a'`, `'e'`
  ASCII sum = 99 (`'c'`) + 97 (`'a'`) + 101 (`'e'`) = **297**

* Character `'e'` occurs only once → ignored

* Character `'d'` occurs only once → ignored

* Character `'c'` also only once → ignored

**Output:** `[197, 297]`

---

### 💡 **Approach & Intuition**

1. **Track First and Last Indices:**

   * Use two arrays of size 26 (for each lowercase letter) to store:

     * `first[i]`: first index of character `i + 'a'`
     * `last[i]`: last index of character `i + 'a'`

2. **Scan the string once** to fill in these positions.

3. **For each character** from `'a'` to `'z'`:

   * If it occurs more than once (i.e., `first[c] < last[c]`), iterate from `first[c]+1` to `last[c]-1` and calculate the sum of ASCII values.
   * If the sum is not zero, add it to the result.

4. **Return** the final list of ASCII sums.

---

### ✅ **Code**

```java
import java.util.*;

class Solution {
    public ArrayList<Integer> asciirange(String s) {
        int[] first = new int[26], last = new int[26];
        Arrays.fill(first, -1);
        Arrays.fill(last, -1);
        ArrayList<Integer> result = new ArrayList<>();
        int n = s.length();

        // Step 1: Store first and last index of each character
        for (int i = 0; i < n; i++) {
            int idx = s.charAt(i) - 'a';
            if (first[idx] == -1) first[idx] = i;
            last[idx] = i;
        }

        // Step 2: Process each character range
        for (int c = 0; c < 26; c++) {
            if (first[c] != -1 && first[c] < last[c]) {
                int sum = 0;
                for (int i = first[c] + 1; i < last[c]; i++) {
                    sum += s.charAt(i);
                }
                if (sum != 0) result.add(sum);
            }
        }

        return result;
    }
}
```

---






