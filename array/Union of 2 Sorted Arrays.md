### ✅ **Problem Explanation**

You're given two **sorted arrays** `a[]` and `b[]` (which may have duplicates). You need to **return a sorted list of distinct elements** present in either array (i.e., union of the two arrays).

---

### 🔎 **Example**

```java
Input: a[] = [1, 2, 3, 4, 5], b[] = [1, 2, 3, 6, 7]
Output: [1, 2, 3, 4, 5, 6, 7]

Input: a[] = [2, 2, 3, 4, 5], b[] = [1, 1, 2, 3, 4]
Output: [1, 2, 3, 4, 5]

Input: a[] = [1, 1, 1, 1, 1], b[] = [2, 2, 2, 2, 2]
Output: [1, 2]
```

---

## ✅ Brute Force Approach (Using Set)

**Logic:**

* Insert all elements from both arrays into a `Set` (which stores only unique elements).
* Then convert the set to a sorted list.

### 🔧 Java Code:

```java
import java.util.*;

public class Solution {
    public static ArrayList<Integer> findUnion(int[] a, int[] b) {
        Set<Integer> set = new HashSet<>();

        // Add elements of first array using normal for loop
        for (int i = 0; i < a.length; i++) {
            set.add(a[i]);
        }

        // Add elements of second array using normal for loop
        for (int i = 0; i < b.length; i++) {
            set.add(b[i]);
        }

        // Convert set to ArrayList and sort it
        ArrayList<Integer> result = new ArrayList<>(set);
        Collections.sort(result);

        return result;
    }
}

```

**🕒 Time Complexity:**

* O(n + m + log(n + m)) where `n` and `m` are sizes of the two arrays.

---

## 🚀 Optimal Approach (Two-Pointer Technique)

**Logic:**

* Traverse both arrays using two pointers `i` and `j`.
* Since arrays are sorted:

  * Compare `a[i]` and `b[j]`
  * Add the smaller value and move forward (avoiding duplicates)
  * If both are equal, add once and move both pointers.

### ✨ Java Code:

```java
import java.util.*;

class Solution {
    public static ArrayList<Integer> findUnion(int[] a, int[] b) {
        ArrayList<Integer> result = new ArrayList<>();
        int i = 0, j = 0;
        int n = a.length, m = b.length;

        while (i < n && j < m) {
            // Skip duplicates in a[]
            while (i > 0 && i < n && a[i] == a[i - 1]) i++;
            // Skip duplicates in b[]
            while (j > 0 && j < m && b[j] == b[j - 1]) j++;

            if (i >= n || j >= m) break;

            if (a[i] < b[j]) {
                result.add(a[i]);
                i++;
            } else if (a[i] > b[j]) {
                result.add(b[j]);
                j++;
            } else {
                result.add(a[i]);
                i++;
                j++;
            }
        }

        // Add remaining elements in a[]
        while (i < n) {
            if (i == 0 || a[i] != a[i - 1]) {
                result.add(a[i]);
            }
            i++;
        }

        // Add remaining elements in b[]
        while (j < m) {
            if (j == 0 || b[j] != b[j - 1]) {
                result.add(b[j]);
            }
            j++;
        }

        return result;
    }

    public static void main(String[] args) {
        int[] a = {2, 2, 3, 4, 5};
        int[] b = {1, 1, 2, 3, 4};

        System.out.println(findUnion(a, b)); // Output: [1, 2, 3, 4, 5]
    }
}
```

---

### 💡 Dry Run for:

```java
a = [2, 2, 3, 4, 5]
b = [1, 1, 2, 3, 4]
```

Steps:

* Compare 2 and 1 → add 1
* Compare 2 and 1 → skip duplicate → add 2
* Compare 2 and 2 → skip duplicate
* Compare 3 and 3 → add 3
* Compare 4 and 4 → add 4
* Only 5 remains → add 5

Output: `[1, 2, 3, 4, 5]`

---

### 📌 Conclusion

| Approach    | Time Complexity  | Space Complexity | Notes                           |
| ----------- | ---------------- | ---------------- | ------------------------------- |
| Brute Force | O(n + m + log n) | O(n + m)         | Uses HashSet and sorting        |
| Two Pointer | O(n + m)         | O(n + m)         | Efficient for **sorted** arrays |
