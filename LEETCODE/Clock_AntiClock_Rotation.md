# Left and Right Array Rotation in Java

This document explains how to perform **left** (anticlockwise) and **right** (clockwise) rotations of an array by one position in Java. It includes well-commented code, step-by-step explanations, and example dry runs.

---

## 1. Left Rotate by One Position (Anticlockwise)

### Code

```java
class Solution {
    // Left Rotate by One Position (anticlockwise)
    public void leftRotate(int arr[], int n) {
        if (n <= 1) return; // No rotation needed for empty/single element

        int first = arr[0]; // Store the first element

        // Shift all elements one position to the left
        for (int i = 0; i < n - 1; i++) {
            arr[i] = arr[i + 1];
        }

        arr[n - 1] = first; // Place first element at the end
    }
}
```

### Step-by-Step Explanation

1. **Check for trivial cases:**  
   If the array has 0 or 1 element, rotation has no effect, so return.

2. **Store the first element:**  
   This is the element that will be moved to the end after shifting.

3. **Shift elements left:**  
   Each element moves to the index before it.

4. **Place the stored element at the end:**  
   The original first element now becomes the last element.

### Dry Run Example

**Before:**  
`arr = [1, 2, 3, 4, 5]`

**Steps:**
- Store `first = arr[0] = 1`
- Shift left:
  - arr[0] = arr[1] → 2
  - arr[1] = arr[2] → 3
  - arr[2] = arr[3] → 4
  - arr[3] = arr[4] → 5
- arr[4] = first → 1

**After:**  
`arr = [2, 3, 4, 5, 1]`

---

## 2. Right Rotate by One Position (Clockwise)

### Code

```java
class Solution {
    // Right Rotate by One Position (clockwise)
    public void rightRotate(int arr[], int n) {
        if (n <= 1) return; // No rotation needed for empty/single element

        int last = arr[n - 1]; // Store the last element

        // Shift all elements one position to the right
        for (int i = n - 1; i > 0; i--) {
            arr[i] = arr[i - 1];
        }

        arr[0] = last; // Place last element at the front
    }
}
```

### Step-by-Step Explanation

1. **Check for trivial cases:**  
   If the array has 0 or 1 element, rotation has no effect, so return.

2. **Store the last element:**  
   This is the element that will be moved to the front after shifting.

3. **Shift elements right:**  
   Each element moves to the index after it.

4. **Place the stored element at the front:**  
   The original last element now becomes the first element.

### Dry Run Example

**Before:**  
`arr = [1, 2, 3, 4, 5]`

**Steps:**
- Store `last = arr[4] = 5`
- Shift right:
  - arr[4] = arr[3] → 4
  - arr[3] = arr[2] → 3
  - arr[2] = arr[1] → 2
  - arr[1] = arr[0] → 1
- arr[0] = last → 5

**After:**  
`arr = [5, 1, 2, 3, 4]`

---

## 3. Time and Space Complexity

- **Time Complexity:** O(n) for both left and right rotation (single pass through the array)
- **Space Complexity:** O(1) (rotations are in-place, no extra array is used)

---

## 4. Notes

- These methods rotate the array **by one position**. To rotate by `k` positions, you can call the method `k` times or use a more efficient algorithm (e.g., reversal algorithm).
- Arrays are modified **in-place**, meaning the input array itself is changed.

---

## 5. Example Usage

```java
public class Demo {
    public static void main(String[] args) {
        int[] arr = {10, 20, 30, 40, 50};
        int n = arr.length;

        Solution sol = new Solution();

        sol.leftRotate(arr, n);
        System.out.println(Arrays.toString(arr)); // [20, 30, 40, 50, 10]

        sol.rightRotate(arr, n);
        System.out.println(Arrays.toString(arr)); // [10, 20, 30, 40, 50]
    }
}
```

---

## 6. Visual Summary

| Operation   | Input         | Output        |
|-------------|--------------|--------------|
| Left Rotate | [1,2,3,4,5]  | [2,3,4,5,1]  |
| Right Rotate| [1,2,3,4,5]  | [5,1,2,3,4]  |

---
