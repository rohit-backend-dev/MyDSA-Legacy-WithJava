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

## ⚡ Optimal Solution

### 🔍 Optimization Idea:

1. First pass: record **first and last indices** of each character using a `Map<Character, int[]>`.
2. Second pass: for characters whose first ≠ last, compute sum from index `first+1` to `last-1`.

### ✅ Time Complexity: `O(N)`, Space: `O(26)` or `O(N)` max.

---

### 🚀 Java Code (Optimal)

```java
import java.util.*;

public class ASCIIRangeSum {
    public static List<Integer> optimalASCII(String s) {
        Map<Character, int[]> map = new HashMap<>();

        // Step 1: Record first and last occurrence
        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            if (!map.containsKey(ch)) {
                map.put(ch, new int[]{i, i});
            } else {
                map.get(ch)[1] = i;
            }
        }

        // Step 2: Compute ASCII sum between first and last index
        List<Integer> result = new ArrayList<>();
        for (Map.Entry<Character, int[]> entry : map.entrySet()) {
            int start = entry.getValue()[0];
            int end = entry.getValue()[1];
            if (start != end) {
                int sum = 0;
                for (int i = start + 1; i < end; i++) {
                    sum += s.charAt(i);
                }
                if (sum > 0) {
                    result.add(sum);
                }
            }
        }

        return result;
    }

    public static void main(String[] args) {
        System.out.println(optimalASCII("abacab")); // [294, 293]
        System.out.println(optimalASCII("acdac"));  // [197, 199]
    }
}
```

---

## ⚡ Further Optimized Approach – Using Prefix Sum

### 🧠 Idea:

1. Precompute a `prefixSum[]` array:

   * `prefixSum[i] = sum of ASCII values from s[0] to s[i-1]`
2. For each character whose first and last index differ:

   * Compute sum using:

     ```
     asciiSum = prefixSum[last] - prefixSum[first + 1]
     ```

### ✅ Time Complexity:

* Preprocessing: `O(N)`
* Sum queries: `O(1)` per character (26 max)
* Overall: `O(N)`

---

## 💡 Why is it Better?

Instead of looping between indices every time, you just **subtract two prefix sums**. Much faster for large strings.

---

## 🧪 Dry Run Example

```text
s = "abacab"
Indices: 0 1 2 3 4 5
String:  a b a c a b
ASCII:   97 98 97 99 97 98

Prefix Sum: [0, 97, 195, 292, 391, 488, 586]
            s[0] to s[0] = 97     → prefixSum[1]
            s[0] to s[1] = 195    → prefixSum[2]
            ...
```

For `'a'`: first=0, last=4
Sum = prefixSum\[4] - prefixSum\[1] = 391 - 97 = **294**

For `'b'`: first=1, last=5
Sum = prefixSum\[5] - prefixSum\[2] = 488 - 195 = **293**

✅ Matches expected results!

---

## 🚀 Java Code with Prefix Sum Optimization

```java
import java.util.*;

public class ASCIIRangeSum {
    public static List<Integer> prefixSumASCII(String s) {
        int n = s.length();
        int[] prefixSum = new int[n + 1]; // prefixSum[i] = sum from s[0] to s[i - 1]

        // Step 1: Build prefix sum of ASCII values
        for (int i = 0; i < n; i++) {
            prefixSum[i + 1] = prefixSum[i] + s.charAt(i);
        }

        // Step 2: Track first and last occurrence of characters
        Map<Character, int[]> map = new HashMap<>();
        for (int i = 0; i < n; i++) {
            char ch = s.charAt(i);
            if (!map.containsKey(ch)) {
                map.put(ch, new int[]{i, i});
            } else {
                map.get(ch)[1] = i;
            }
        }

        // Step 3: Use prefix sum to calculate ASCII range sum
        List<Integer> result = new ArrayList<>();
        for (Map.Entry<Character, int[]> entry : map.entrySet()) {
            int first = entry.getValue()[0];
            int last = entry.getValue()[1];
            if (first != last) {
                int sum = prefixSum[last] - prefixSum[first + 1];
                if (sum > 0) result.add(sum);
            }
        }

        return result;
    }

    public static void main(String[] args) {
        System.out.println(prefixSumASCII("abacab")); // [294, 293]
        System.out.println(prefixSumASCII("acdac"));  // [199, 197]
    }
}
```

---

## ✅ When to Use This Optimization

* ✅ For long strings (e.g. 10⁶ characters)
* ✅ When you have to calculate range sums multiple times
* ✅ When performance matters

---




