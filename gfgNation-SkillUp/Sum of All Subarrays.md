# Sum of All Subarrays

## Problem Statement

Given an integer array `arr[]`, compute the sum of all possible subarrays of the array.  
A subarray is a contiguous part of the array.

---

## Examples

**Example 1:**

- **Input:** `arr[] = [1, 4, 5, 3, 2]`
- **Output:** `116`
- **Explanation:**  
  The sum of all possible subarrays of the array `[1, 4, 5, 3, 2]` is `116`.

**Example 2:**

- **Input:** `arr[] = [1, 2, 3, 4]`
- **Output:** `50`
- **Explanation:**  
  The sum of all possible subarrays of the array `[1, 2, 3, 4]` is `50`.

---

## Approach

To efficiently compute the sum of all subarrays, we use a mathematical formula.  
For each element at index `i`, the number of subarrays in which `arr[i]` appears is `(i + 1) * (n - i)` where:
- `i + 1` is the number of choices for the starting index (from 0 to i)
- `n - i` is the number of choices for the ending index (from i to n-1)
- So, each `arr[i]` contributes `arr[i] * (i + 1) * (n - i)` to the total sum.

---

## Edge Cases

- **Empty array:** The sum is 0 as there are no subarrays.
- **Single element array:** The sum is the element itself.
- **All elements are the same:** The formula still applies, and each identical element contributes according to its position.
- **Array with negative numbers:** Negative numbers are included as normal, and their contributions can reduce the total sum.
- **Large arrays:** This approach is efficient for large inputs due to its O(N) complexity.
- **Array with zeros:** Zeros contribute nothing, but their count in subarrays is still considered.

---

## Implementation

```java
class GfG {
 
    static int subarraySum(int[] arr) {
        int n = arr.length;
        int result = 0;

        // Compute sum of subarrays using the formula
        for (int i = 0; i < n; i++) {
            result += (arr[i] * (i + 1) * (n - i));
        }

        // Return the sum of all subarrays
        return result;
    }

    public static void main(String[] args) {
        int[] arr1 = {1, 4, 5, 3, 2};
        System.out.println(subarraySum(arr1)); // Output: 116

        int[] arr2 = {1, 2, 3, 4};
        System.out.println(subarraySum(arr2)); // Output: 50

        int[] arr3 = {};
        System.out.println(subarraySum(arr3)); // Output: 0

        int[] arr4 = {7};
        System.out.println(subarraySum(arr4)); // Output: 7

        int[] arr5 = {0, 0, 0};
        System.out.println(subarraySum(arr5)); // Output: 0

        int[] arr6 = {-1, -2, -3};
        System.out.println(subarraySum(arr6)); // Output: -20
    }
}
```

---

## Time Complexity

- **O(N)** where N is the length of the array, since we iterate through the array once.

## Space Complexity

- **O(1)** — only constant extra space is used.

---

## Notes

- This approach is much faster than generating all possible subarrays explicitly.
- The formula leverages the fact that every element's contribution can be counted directly.
- Handles negative numbers, zeros, and all edge cases efficiently.
