# 📘 Checking if an Array is Sorted

---

## ✅ **Solution 1: Iterative Adjacent Comparison**

### **Idea**

* Traverse the array from the second element (`i=1`) to the last.
* Compare each element with its **previous element** (`arr[i-1]`).
* If any `arr[i] < arr[i-1]`, the array is **not sorted in ascending order**.
* If the loop completes, the array is sorted.

### **Code**

```java
class Solution {
    public boolean isSorted(int[] arr) {
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] < arr[i - 1]) {
                return false; // order violated
            }
        }
        return true;
    }
}
```

### **Example**

* Input: `[1, 2, 3, 5]` → returns `true`
* Input: `[1, 4, 2, 5]` → returns `false`

### **Complexity**

* **Time Complexity:** `O(n)` → single traversal
* **Space Complexity:** `O(1)` → only uses loop variable

---

## ✅ **Solution 2: Recursive Check**

### **Idea**

* A recursive function checks if the **last element** is greater than or equal to the second last.
* If not, return `false`.
* Otherwise, recursively check the smaller subarray.
* Base case: arrays of size `0` or `1` are always sorted.

### **Code**

```java
class Solution {
    public boolean isSorted(int[] arr) {
        return check(arr, arr.length);
    }

    private boolean check(int[] arr, int n) {
        if (n == 1 || n == 0) return true; // base case
        if (arr[n - 1] < arr[n - 2]) return false; // violation
        return check(arr, n - 1); // recursive step
    }
}
```

### **Example**

* Input: `[2, 4, 6, 8]`

  * check last two: `8 >= 6` → ok
  * then `[2,4,6]` … continues → returns `true`

* Input: `[5, 3, 4]`

  * check last two: `4 >= 3` → ok
  * then `[5,3]` → `3 < 5` → returns `false`

### **Complexity**

* **Time Complexity:** `O(n)` → each element checked once
* **Space Complexity:** `O(n)` → due to recursive call stack



Do you want me to also include the **“check both ascending and descending order”** version in the docs so it handles both cases in one function?
