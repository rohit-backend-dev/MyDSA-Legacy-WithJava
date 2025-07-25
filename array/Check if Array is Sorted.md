# Check if Array is Sorted

## Problem Statement

Given an array `arr[]`, check whether it is sorted in non-decreasing order.  
Return `true` if it is sorted, otherwise return `false`.

---

## Examples

### Example 1
**Input:**  
`arr[] = [10, 20, 30, 40, 50]`  
**Output:**  
`true`  
**Explanation:**  
The given array is sorted.

### Example 2
**Input:**  
`arr[] = [90, 80, 100, 70, 40, 30]`  
**Output:**  
`false`  
**Explanation:**  
The given array is not sorted.

---

## Constraints

- 1 ≤ arr.size ≤ 10^6
- -10^9 ≤ arr[i] ≤ 10^9

---

## Edge Cases Handled

- Single element array → always sorted ✅
- Duplicates allowed (non-decreasing) ✅
- Large input sizes (up to 10^6) ✅

---

## Explanation

- We check each element with its previous element.
- If any element is smaller than the previous one, the array is not sorted.
- **Start the loop from i=1** to avoid accessing `arr[-1]`, which would cause an IndexOutOfBoundsException in Java.

---

## Java Solution

```java
class Solution {
    public boolean isSorted(int[] arr) {
        int n = arr.length;

        for (int i = 1; i < n; i++) { // Start from 1
            if (arr[i] < arr[i - 1]) {
                return false; // Found a decreasing pair
            }
        }

        return true; // No violations found
    }

    public static void main(String[] args) {
        Solution sol = new Solution();

        // Test Cases
        System.out.println(sol.isSorted(new int[]{10, 20, 30, 40, 50}));  // true
        System.out.println(sol.isSorted(new int[]{90, 80, 100, 70, 40})); // false
        System.out.println(sol.isSorted(new int[]{5}));                   // true (single element)
        System.out.println(sol.isSorted(new int[]{-10, -10, 0, 5, 5}));   // true (with duplicates)
    }
}
```

---

## Time & Space Complexity

- **Time Complexity:** O(n)
- **Space Complexity:** O(1)

---

## Why Loop Starts at i=1

- If you start at i=0 and check `arr[i-1]`, you access `arr[-1]` (invalid index).
- Starting at i=1 allows comparing each element with its predecessor safely.

| i Start | Accessed Indices     | Valid? | Why?                     |
|---------|----------------------|--------|--------------------------|
| 0       | arr[i-1] = arr[-1]   | ❌     | Invalid index            |
| 1       | arr[1] and arr[0]    | ✅     | Valid comparison         |

---

## Logic

The array is sorted in non-decreasing order if:

```java
arr[i] >= arr[i - 1] for all i from 1 to n-1
```

---
