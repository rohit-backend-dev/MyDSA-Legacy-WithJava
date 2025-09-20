## 🔹 Problem

We want to find the element that appears **more than n/2 times** in an array of size `n`.
👉 If guaranteed such an element exists (like in LeetCode 169: *Majority Element*), Boyer–Moore works perfectly.

---

## 🔹 Idea

* Maintain a **candidate** and a **count**.
* Traverse the array:

  1. If `count == 0`, set the current number as `candidate`.
  2. If the current number equals the `candidate`, increment `count`.
  3. Else, decrement `count`.
* After one pass, `candidate` will hold the majority element.

---

## 🔹 Java Code

```java
class Solution {
    public int majorityElement(int[] nums) {
        int candidate = 0, count = 0;

        for (int num : nums) {
            if (count == 0) {
                candidate = num;
            }
            if (num == candidate) {
                count++;
            } else {
                count--;
            }
        }
        
        return candidate;
    }
}
```

## 🔹 Complexity

* **Time**: `O(n)` (single pass)
* **Space**: `O(1)` (no extra structures)
