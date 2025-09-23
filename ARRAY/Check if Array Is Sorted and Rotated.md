**LeetCode 1752: Check if Array Is Sorted and Rotated** 

### Intuition

* If an array is sorted and rotated, then there should be **at most one place** where `nums[i] > nums[i+1]`.

  * Example: `[3,4,5,1,2]` → only at `5 > 1`.
* If there are more than one such places, it’s not sorted & rotated.

---

### Optimized Java Solution

```java
class Solution {
    public boolean check(int[] nums) {
        int n = nums.length;
        int count = 0;

        for (int i = 0; i < n; i++) {
            if (nums[i] > nums[(i + 1) % n]) {
                count++;
            }
            if (count > 1) return false; // more than one drop => not valid
        }

        return true;
    }
}
```

---

### Explanation

* We loop over the array.
* Compare each `nums[i]` with `nums[(i+1) % n]` (circular check).
* Count how many times the sequence decreases.
* If it decreases **more than once**, return `false`.
* Otherwise, return `true`.

---

✅ **Time Complexity:** `O(n)`
✅ **Space Complexity:** `O(1)`

