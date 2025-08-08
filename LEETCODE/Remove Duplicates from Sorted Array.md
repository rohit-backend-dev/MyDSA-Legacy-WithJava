# Remove Duplicates from Sorted Array

## Problem Statement

Given an integer array `nums` sorted in non-decreasing order, remove the duplicates **in-place** so that each unique element appears only once.  
The relative order of the elements should be kept the same.  
Return the number of unique elements, `k`.  
Modify the array such that the first `k` elements are the unique values.  
The remaining elements do not matter.

---

## Example 1

**Input:**  
`nums = [1,1,2]`  
**Output:**  
`2, nums = [1,2,_]`  
**Explanation:**  
Your function should return `k = 2`, with the first two elements being 1 and 2 respectively.

---

## Example 2

**Input:**  
`nums = [0,0,1,1,1,2,2,3,3,4]`  
**Output:**  
`5, nums = [0,1,2,3,4,_,_,_,_,_]`  
**Explanation:**  
Your function should return `k = 5`, with the first five elements being 0, 1, 2, 3, 4.

---

## Approaches

### 1. Brute Force (Not Accepted – Uses Extra Space)
- Uses a Set to collect unique elements, then rewrites the array.
- **Time:** O(n)
- **Space:** O(n) (not in-place, violates constraints)

```java
public int removeDuplicates(int[] nums) {
    Set<Integer> set = new LinkedHashSet<>();
    for (int num : nums) set.add(num);

    int i = 0;
    for (int num : set) {
        nums[i++] = num;
    }

    return set.size();
}
```
- Easy, but **NOT accepted** in interviews/Leetcode due to space usage.

---

### 2. Better Approach (Optimal Two-Pointer Technique)
- Use two pointers:
  - `i` (slow): points to last unique value
  - `j` (fast): scans the array
- If `nums[j] != nums[i]`, increment `i` and set `nums[i] = nums[j]`.

```java
public int removeDuplicates(int[] nums) {
    if (nums.length == 0) return 0;

    int i = 0;
    for (int j = 1; j < nums.length; j++) {
        if (nums[j] != nums[i]) {
            i++;
            nums[i] = nums[j];
        }
    }
    return i + 1;
}
```

#### Example Walkthrough
For `nums = [1,1,2]`:
- i=0, j=1: nums[1]==nums[0] → skip
- j=2: nums[2]!=nums[0] → i++, nums[1]=nums[2] → [1,2,2]
- Return `i+1 = 2`

---

## Complexity Table

| Approach     | Time    | Space | Notes                 |
|--------------|---------|-------|-----------------------|
| Brute Force  | O(n)    | O(n)  | Uses Set; not in-place|
| Better       | O(n)    | O(1)  | Two-pointer; accepted |
| Optimal      | O(n)    | O(1)  | Same as Better        |

---

## Final Tip

- For in-place modification on sorted arrays, always use the two-pointer technique.
- The brute force approach is **not accepted** for this Leetcode problem.

---
