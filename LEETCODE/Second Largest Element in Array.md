# Second Largest Element in Array

## Problem Statement

Given an array of positive integers `arr[]`, return the second largest element from the array.  
If the second largest element doesn't exist (i.e., all elements are equal), return `-1`.

**Note:**  
The second largest element should not be equal to the largest element.

---

## Examples

### Example 1
**Input:**  
`arr[] = [12, 35, 1, 10, 34, 1]`  
**Output:**  
`34`  
**Explanation:**  
The largest element is 35 and the second largest is 34.

### Example 2
**Input:**  
`arr[] = [10, 5, 10]`  
**Output:**  
`5`  
**Explanation:**  
The largest element is 10 and the second largest is 5.

### Example 3
**Input:**  
`arr[] = [10, 10, 10]`  
**Output:**  
`-1`  
**Explanation:**  
All elements are equal so there is no second largest.

---

## Constraints

- 2 ≤ arr.size() ≤ 10^5
- 1 ≤ arr[i] ≤ 10^5

---

## Expected Time and Space Complexity

- **Time Complexity:** O(n)
- **Auxiliary Space:** O(1)

---

## Approaches

### 1. Brute Force (Sorting)  
Sort the array and scan from the end for the first element less than the largest.

- **Time Complexity:** O(n log n)  
- **Space Complexity:** O(1)

```java
import java.util.Arrays;

class SolutionBruteForce {
    public static int secondLargest(int[] arr) {
        int n = arr.length;
        Arrays.sort(arr); // Sort the array
        int largest = arr[n - 1];

        // Find the first element less than the largest from the end
        for (int i = n - 2; i >= 0; i--) {
            if (arr[i] < largest) {
                return arr[i];
            }
        }
        return -1; // No second largest exists
    }

    public static void main(String[] args) {
        System.out.println(secondLargest(new int[]{12, 35, 1, 10, 34, 1}));  // 34
        System.out.println(secondLargest(new int[]{10, 5, 10}));            // 5
        System.out.println(secondLargest(new int[]{10, 10, 10}));           // -1
    }
}
```

---

### 2. Better Approach – Two Passes  
First pass to find the largest, second pass for the second largest.  
- **Time Complexity:** O(n)  
- **Space Complexity:** O(1)

```java
public class SolutionBetter {
    public static int secondLargest(int[] arr) {
        int n = arr.length;

        int largest = Integer.MIN_VALUE;
        for (int i = 0; i < n; i++) {
            if (arr[i] > largest) {
                largest = arr[i];
            }
        }

        int secondLargest = Integer.MIN_VALUE;
        for (int i = 0; i < n; i++) {
            if (arr[i] > secondLargest && arr[i] < largest) {
                secondLargest = arr[i];
            }
        }

        return (secondLargest == Integer.MIN_VALUE) ? -1 : secondLargest;
    }
}
```

---

### 3. Optimal Approach – One Pass  
Track both largest and second largest in a single traversal.  
- **Time Complexity:** O(n)  
- **Space Complexity:** O(1)

```java
public class SolutionOptimal {
    public static int secondLargest(int[] arr) {
        int largest = Integer.MIN_VALUE;
        int secondLargest = Integer.MIN_VALUE;

        for (int num : arr) {
            if (num > largest) {
                secondLargest = largest;
                largest = num;
            } else if (num > secondLargest && num < largest) {
                secondLargest = num;
            }
        }

        return (secondLargest == Integer.MIN_VALUE) ? -1 : secondLargest;
    }
}
```

---

## Summary Table

| Approach           | Time        | Space | Notes                              |
|:-------------------|:------------|:------|:-----------------------------------|
| Brute Force        | O(n log n)  | O(1)  | Uses sorting                       |
| Better (2-pass)    | O(n)        | O(1)  | Two traversals                     |
| Optimal (1-pass)   | O(n)        | O(1)  | Best — single pass, constant space |

---
