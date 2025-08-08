### 🔍 **Linear Search** – Simplest Searching Algorithm

---

### ✅ **What is Linear Search?**

Linear Search is a technique to **find an element** in an array by checking **each element one by one** from start to end.

---

### 📌 **How it Works:**

* Start from the first element.
* Compare each element with the target.
* If found, return the index.
* If not found after full loop, return -1.

---

### 🧠 **Time Complexity:**

| Case       | Time |
| ---------- | ---- |
| Best Case  | O(1) |
| Worst Case | O(n) |
| Space      | O(1) |

---

### ✅ **Java Code:**

```java
public int linearSearch(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == target) {
            return i; // Element found at index i
        }
    }
    return -1; // Not found
}
```

---

### 🔢 Example:

```java
Input: arr = [5, 3, 7, 2, 9], target = 2  
Output: 3  // (2 is at index 3)
```

---
