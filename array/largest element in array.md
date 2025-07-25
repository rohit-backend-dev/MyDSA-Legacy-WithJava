# Largest Element in Array (BASIC)

## Problem Statement

Given an array `arr[]`, the task is to find the largest element and return it.

## Examples

### Example 1

**Input:**  
`arr[] = [1, 8, 7, 56, 90]`  
**Output:**  
`90`  
**Explanation:**  
The largest element of the given array is 90.

### Example 2

**Input:**  
`arr[] = [5, 5, 5, 5]`  
**Output:**  
`5`  
**Explanation:**  
The largest element of the given array is 5.

### Example 3

**Input:**  
`arr[] = [10]`  
**Output:**  
`10`  
**Explanation:**  
There is only one element which is the largest.

## Constraints

- 1 <= arr.size() <= 10^6
- 0 <= arr[i] <= 10^6

## Solution

Below is a sample solution in Java:

```java
class Solution {
    public static int largest(int[] arr) {
        // Get the length of the array
        int n = arr.length;

        // Initialize 'largest' with the first element of the array
        int largest = arr[0];

        // Iterate through the array to find the largest element
        for(int i = 0; i < n; i++) {
            if(arr[i] > largest) {
                largest = arr[i];
            }
        }
        // Return the largest element
        return largest;
    }
}
```

### Explanation

- The function `largest` takes an integer array `arr` as input.
- It initializes a variable `largest` with the first element of the array.
- It iterates through the array, comparing each element with `largest`.
- If a larger element is found, it updates `largest`.
- Finally, it returns the largest element found in the array.

## Notes

- The algorithm runs in O(n) time, where n is the size of the array.
- It is efficient for very large arrays as per the given constraints.
