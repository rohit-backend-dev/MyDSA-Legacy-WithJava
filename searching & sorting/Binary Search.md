## ✅ Iterative Binary Search

```java
class Solution {
    // Iterative Binary Search
    // Time Complexity: O(log n)
    // Space Complexity: O(1)
    public int binarySearch(int[] arr, int target) {
        int low = 0, high = arr.length - 1;

        while (low <= high) {
            int mid = low + (high - low) / 2; // prevents overflow

            if (arr[mid] == target) {
                return mid; // found
            } else if (arr[mid] < target) {
                low = mid + 1; // search right
            } else {
                high = mid - 1; // search left
            }
        }
        return -1; // not found
    }
}
```

---

## ✅ Recursive Binary Search

```java
class Solution {
    // Recursive Binary Search
    // Time Complexity: O(log n)
    // Space Complexity: O(log n) due to recursion stack
    public int binarySearch(int[] arr, int low, int high, int target) {
        if (low <= high) {
            int mid = low + (high - low) / 2;

            if (arr[mid] == target) {
                return mid; // found
            } else if (arr[mid] < target) {
                return binarySearch(arr, mid + 1, high, target); // right half
            } else {
                return binarySearch(arr, low, mid - 1, target); // left half
            }
        }
        return -1; // not found
    }
}
```

---

## ⏱️ Time Complexity

* **Best Case:** `O(1)` (when the middle element is the target)
* **Average/Worst Case:** `O(log n)` (search space halves each step)

## 🗂️ Space Complexity

* **Iterative:** `O(1)` (constant extra variables)
* **Recursive:** `O(log n)` (recursion stack depth)
