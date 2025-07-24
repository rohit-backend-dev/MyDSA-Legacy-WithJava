# Smallest Missing Positive Number

## Problem Statement

Given an unsorted array `arr[]` containing both positive and negative integers (including zero and duplicates), find the **smallest positive integer** (greater than 0) that is missing from the array.

---

## Examples

### Example 1
**Input:**  
`arr[] = [2, -3, 4, 1, 1, 7]`  
**Output:**  
`3`  
**Explanation:**  
The positive integers present are 1, 2, 4, 7. The smallest missing positive is **3**.

---

### Example 2
**Input:**  
`arr[] = [5, 3, 2, 5, 1]`  
**Output:**  
`4`  
**Explanation:**  
The positive integers present are 1, 2, 3, 5. The smallest missing positive is **4**.

---

### Example 3
**Input:**  
`arr[] = [-8, 0, -1, -4, -3]`  
**Output:**  
`1`  
**Explanation:**  
There are no positive integers, so the smallest missing positive is **1**.

---

## Approach

The goal is to find the smallest positive integer **not present** in the array.  
The most efficient solution runs in O(n) time and O(1) space (ignoring input array modifications).

### Steps:
1. **Ignore non-positive numbers and numbers greater than n:**  
   For an array of size n, the smallest missing positive number must be in the range `[1, n+1]`.
2. **Place each number in its correct index (if possible):**  
   Try to place the value `x` at index `x-1` if `1 <= x <= n`.
3. **Scan for the first index where `arr[i] != i+1`:**  
   That position indicates the missing number.
4. **If all positions are filled correctly, then the missing number is `n+1`.**

---

## Edge Cases

- **All elements are negative or zero:**  
  Example: `[-3, -1, 0]` → Output: `1`
- **Array with continuous positives from 1:**  
  Example: `[1, 2, 3, 4]` → Output: `5`
- **Array with duplicates:**  
  Example: `[1, 2, 2, 3]` → Output: `4`
- **Array with large numbers:**  
  Example: `[1, 100, 2000]` → Output: `2`
- **Empty array:**  
  Example: `[]` → Output: `1`
- **Array with only one value:**  
  Example: `[1]` → Output: `2`,  
  Example: `[2]` → Output: `1`
- **Array with all values the same:**  
  Example: `[1, 1, 1]` → Output: `2`
- **Array with all positive numbers but not starting from 1:**  
  Example: `[2, 3, 4]` → Output: `1`

---

## Solution (Java Example)

```java
class Solution {
    public int missingNumber(int[] arr) {
        int n = arr.length;

        // Place each number in its correct index if possible
        for (int i = 0; i < n; i++) {
            while (arr[i] > 0 && arr[i] <= n && arr[i] != arr[arr[i] - 1]) {
                // Swap arr[i] with arr[arr[i] - 1]
                int correctIndex = arr[i] - 1;
                int temp = arr[i];
                arr[i] = arr[correctIndex];
                arr[correctIndex] = temp;
            }
        }

        // Find the first location where index + 1 != value
        for (int i = 0; i < n; i++) {
            if (arr[i] != i + 1) {
                return i + 1;
            }
        }

        // All values are in their correct place, so the missing number is n+1
        return n + 1;
    }
}
```

---

## Complexity Analysis

- **Time Complexity:** O(n), each element is swapped at most once.
- **Space Complexity:** O(1), in-place rearrangement.

---

## Additional Notes

- The algorithm works even if the array contains duplicates, negative numbers, and zero.
- Modifies the input array. If preservation is needed, copy the array first.
