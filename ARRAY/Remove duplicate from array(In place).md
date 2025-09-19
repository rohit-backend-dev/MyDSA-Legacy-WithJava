## ✅ Optimal Solution 1: Two Pointers (Best in Practice)

### Code

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums.length == 0) return 0;

        int i = 0;  // slow pointer
        for (int j = 1; j < nums.length; j++) {
            if (nums[j] != nums[i]) {
                i++;
                nums[i] = nums[j]; // overwrite duplicate
            }
        }
        return i + 1; // new length
    }
}
```


## Step by Step explanation:

* At first, the first fan is always allowed in → i = 0.
* Now j starts checking from seat 1.
* If nums[j] == nums[i] → this fan is a duplicate, so they’re ignored (not moved forward).
* If nums[j] != nums[i] → 🎉 new unique fan found!
* Move i forward (i++) to open the next available seat.
* Seat this new fan at nums[i].
* Continue until everyone is checked.

### Explanation

* Use two pointers (`i` for unique index, `j` for scanning).
* Whenever a new number is found (`nums[j] != nums[i]`), place it at the next position.
* The part of the array from `0` to `i` will be the **unique elements**.

Example:
`[1,1,2,3,3]` → after process → `[1,2,3,…]` and returns `3`.

### Complexity

* **Time Complexity:** O(n) (single pass).
* **Space Complexity:** O(1) (in-place, no extra data structure).

---

## ✅ Solution 2: Using a HashSet (Not In-Place)

### Code

```java
import java.util.*;

class Solution {
    public int removeDuplicates(int[] nums) {
        Set<Integer> set = new LinkedHashSet<>(); // maintains insertion order
        for (int num : nums) {
            set.add(num);
        }
        
        int index = 0;
        for (int num : set) {
            nums[index++] = num; // overwrite nums with unique values
        }
        
        return set.size(); // new length
    }
}
```

### Explanation

* HashSet removes duplicates.
* LinkedHashSet is used so the order is preserved.
* Copy back unique values into the original array.

### Complexity

* **Time Complexity:** O(n).
* **Space Complexity:** O(n) (extra set storage).

