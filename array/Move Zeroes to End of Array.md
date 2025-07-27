# Move Zeroes to End of Array

## Problem Statement

Given an integer array `nums`, move all the `0`'s to the end of it while maintaining the relative order of the non-zero elements. The operation should be **in-place** if possible.

- Note that you must do this in-place without making a copy of the array.
**Example:**
```
Input:  [0, 1, 0, 3, 12]
Output: [1, 3, 12, 0, 0]
```

---

## Approach 1: Brute Force (Using Extra Space)

### Idea

- Create a temporary list to store all non-zero elements.
- Fill the rest of the list with zeroes to match the original array's size.
- Copy the result back to the original array.

### Java Code

```java
public void moveZeroesBruteForce(int[] nums) {
    List<Integer> temp = new ArrayList<>();
    // Step 1: Add non-zero elements
    for (int i = 0; i < nums.length; i++) {
        if (nums[i] != 0) {
            temp.add(nums[i]);
        }
    }
    // Step 2: Add zeros to match original size
    while (temp.size() < nums.length) {
        temp.add(0);
    }
    // Step 3: Copy back to original array
    for (int i = 0; i < nums.length; i++) {
        nums[i] = temp.get(i);
    }
}
```

### Line-by-Line Explanation

1. **Create a temporary list:**  
   `List<Integer> temp = new ArrayList<>();`  
   Stores non-zero elements temporarily.
2. **Copy non-zero elements:**  
   Loop through `nums`. If the element is not zero, add it to `temp`.  
   `if (nums[i] != 0) temp.add(nums[i]);`
3. **Fill with zeros:**  
   While `temp` is smaller than the original array, add zeros at the end.  
   `while (temp.size() < nums.length) temp.add(0);`
4. **Copy back:**  
   Copy elements from `temp` back to `nums`.
   `nums[i] = temp.get(i);`

### Complexity

- **Time:** O(n)
- **Space:** O(n) (extra space for temporary list)
- **In-place:** ❌

---

## Approach 2: Optimal - In-place, Two Pointers (Overwrite)

### Idea

- Use two pointers:
  - `i`: iterates over the array
  - `j`: tracks the position to place the next non-zero
- First, fill non-zero values at the front, then fill the rest with zeros.

### Java Code

```java
public void moveZeroesOptimal(int[] nums) {
    int j = 0; // position for next non-zero
    // Move non-zeros forward
    for (int i = 0; i < nums.length; i++) {
        if (nums[i] != 0) {
            nums[j] = nums[i];
            j++;
        }
    }
    // Fill remaining with zeros
    while (j < nums.length) {
        nums[j] = 0;
        j++;
    }
}
```

### Line-by-Line Explanation

1. **Set `j = 0`:**  
   Marks the index to place the next non-zero value.
2. **First pass (`for` loop):**  
   - If `nums[i] != 0`, copy it to `nums[j]`, then increment `j`.
   - This collects all non-zero values at the front.
3. **Second pass (`while` loop):**  
   - Fill the rest of the array with zeros from index `j` onwards.

### Dry Run

For input: `[0, 1, 0, 3, 12]`

| i | nums[i] | j | Array State         |
|---|---------|---|---------------------|
| 0 |    0    | 0 | [0, 1, 0, 3, 12]    |
| 1 |    1    | 0 | [1, 1, 0, 3, 12]    |
| 2 |    0    | 1 | [1, 1, 0, 3, 12]    |
| 3 |    3    | 1 | [1, 3, 0, 3, 12]    |
| 4 |   12    | 2 | [1, 3, 12, 3, 12]   |

After loop, fill from `j=3`:  
Final: `[1, 3, 12, 0, 0]`

---

## Approach 3: Optimal - In-place, Single-Pass Swap (When Order Must Be Strictly Preserved)

### Idea

- Use two pointers:
  - `i`: iterates over the array
  - `j`: tracks the leftmost zero
- Swap only when a non-zero is found at `i != j`

### Java Code

```java
public void moveZeroesSwap(int[] nums) {
    int j = 0; // Position of leftmost zero
    for (int i = 0; i < nums.length; i++) {
        if (nums[i] != 0) {
            if (i != j) {
                int temp = nums[i];
                nums[i] = nums[j];
                nums[j] = temp;
            }
            j++;
        }
    }
}
```

### Line-by-Line Explanation

1. **Set `j = 0`:**  
   Tracks where the next non-zero should be swapped.
2. **Loop over array:**  
   If `nums[i] != 0`:
   - If `i != j`, swap `nums[i]` and `nums[j]`
   - Increment `j`
3. **Result:**  
   All non-zeros are moved forward. Zeros are moved to the end with minimal swaps.

### Dry Run

Input: `[0, 1, 0, 3, 12]`

| i | nums[i] | j | Array State         | Swap?      |
|---|---------|---|---------------------|------------|
| 0 |   0     | 0 | [0, 1, 0, 3, 12]    | No         |
| 1 |   1     | 0 | [1, 0, 0, 3, 12]    | Yes (1,0)  |
| 2 |   0     | 1 | [1, 0, 0, 3, 12]    | No         |
| 3 |   3     | 1 | [1, 3, 0, 0, 12]    | Yes (3,0)  |
| 4 |  12     | 2 | [1, 3, 12, 0, 0]    | Yes (12,0) |

Final: `[1, 3, 12, 0, 0]`

---

## Comparison Table

| Approach      | Time   | Space | In-Place | Stable | Extra Notes                  |
|---------------|--------|-------|----------|--------|------------------------------|
| Brute Force   | O(n)   | O(n)  | ❌       | ✅     | Uses extra space             |
| Overwrite     | O(n)   | O(1)  | ✅       | ✅     | Two passes                   |
| Swap (1-pass) | O(n)   | O(1)  | ✅       | ✅     | Fewer writes, more optimal   |

---

## Key Takeaways

- **Overwrite Approach:** Minimal writes if zeros are rare, preserves order, two passes, very simple.
- **Swap Approach:** Fewer total writes if zeros are common, preserves order, one pass.
- **Brute Force:** Useful for learning, not for production due to extra space.

---

## References

- [LeetCode 283. Move Zeroes](https://leetcode.com/problems/move-zeroes/)
- [Java ArrayList Documentation](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html)

---

## Example Test Case

```java
int[] nums = {0, 1, 0, 3, 12};
moveZeroesOptimal(nums);
// nums is now [1, 3, 12, 0, 0]
```

---

**Choose the optimal approach based on space constraints and write efficiency needs. Both optimal methods are in-place and stable.**
