
## **1️⃣ Using Extra Variable**

```java
class Solution {
    public void rotate(int[] arr) {
        int n = arr.length;
        int temp = arr[n - 1];  // store last element
        // shift elements to right
        for (int i = n - 1; i > 0; i--) {
            arr[i] = arr[i - 1];
        }
        arr[0] = temp;  // put last element at first
    }
}
```

**Explanation:**

* Store the last element in `temp`.
* Shift all elements to the right by 1.
* Place the stored last element at the first position.

**Time Complexity:** `O(n)`
**Space Complexity:** `O(1)`

✅ Simple and intuitive.

---

## **2️⃣ Using Reverse Method (In-place, Efficient for k Rotations)**

```java
class Solution {
    public void rotate(int[] arr) {
        int n = arr.length;
        // reverse whole array
        reverse(arr, 0, n - 1);
        // reverse first element (new first element after rotation)
        reverse(arr, 0, 0);
        // reverse remaining elements
        reverse(arr, 1, n - 1);
    }

    private void reverse(int[] arr, int start, int end) {
        while (start < end) {
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;
            start++;
            end--;
        }
    }
}
```

**Explanation:**

* Reverse the whole array.
* Reverse the first `k` elements (here `k = 1`).
* Reverse the remaining elements.

**Time Complexity:** `O(n)`
**Space Complexity:** `O(1)`

✅ Very useful if you want to **rotate by `k` positions** in general.



---
 you want me to show that?
