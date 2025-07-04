# 🚀 Two Pointers Technique

The **Two Pointers** technique is a powerful and versatile approach in algorithmic problem-solving. It involves maintaining two "pointers" (usually indices or iterators) to traverse a data structure (commonly an array, string, or linked list) from different directions or at different speeds. This technique transforms many brute-force O(n²) problems into efficient O(n) solutions.

---

## ✅ When to Use Two Pointers

Two Pointers shine in problems with the following characteristics:

1. **Sorted Arrays or Strings**
   - Predictable movement: Increment/decrement pointers based on comparison.
   - *Example*: 2Sum in sorted array, Container With Most Water.

2. **Finding Pairs, Triplets, or Subarrays With a Condition**
   - Target sum/product, difference, or other constraints.
   - *Examples*: 2Sum, 3Sum, Subarray Product Less Than K.

3. **In-place Modification or Removal**
   - Move elements without extra space; overwrite duplicates or filter elements.
   - *Examples*: Remove Duplicates, Move Zeroes.

4. **Merging or Comparing Two Sequences**
   - Efficient merging or intersection of sorted arrays/strings.
   - *Examples*: Merge Sorted Array, Intersection of Two Arrays.

5. **Optimizing for Subarray/Substring Length**
   - Sliding window for minimum/maximum length with constraints.
   - *Examples*: Minimum Size Subarray Sum, Longest Substring Without Repeating Characters.

6. **Replacing Nested Loops (O(n²))**
   - Check all pairs/subarrays with O(n) or O(n log n).
   - *Examples*: Count pairs with sum < target.

7. **Finding or Counting Palindromes, Valid Patterns**
   - Expand around center, validate substrings.
   - *Examples*: Valid Palindrome, Longest Palindromic Substring.

8. **Finding K-th Element or Merging Streams**
   - Efficiently combine sorted sources.
   - *Examples*: Median of Two Sorted Arrays.

9. **Counting/Collecting Elements Matching a Condition**
   - Collect elements <, >, ==, etc.
   - *Examples*: Count pairs with sum < target.

10. **Handling Overlapping Intervals, Ranges, or Windows**
    - Merge or find overlaps efficiently.
    - *Examples*: Merge Intervals, Meeting Rooms II.

11. **Linked List Cycle Detection or Middle Node**
    - Tortoise and Hare (fast/slow pointers).
    - *Examples*: Floyd’s Cycle Detection, Middle of Linked List.

12. **Two-Pass Operations**
    - Forward and backward scans; converging from both ends.
    - *Examples*: Trapping Rain Water.

13. **Balancing, Pairing, or Equalizing**
    - Split arrays, equalize sums, pair elements.
    - *Examples*: Pairing socks, Split Array.

14. **Simulating Two Agents/Objects Moving**
    - Chasing, merging, aligning, or “race” logic.
    - *Examples*: Race car, pursuit problems.

> **💡 PRO TIP:** If a problem looks like it can be brute-forced by checking all pairs or subarrays, think about how Two Pointers could help reduce complexity.

---

## 🔥 Two Pointers Patterns

### 1. Opposite Ends (Start and End)
**Use case:** Find pairs in sorted array, e.g. 2Sum, Container With Most Water

```java
int left = 0, right = arr.length - 1;
while (left < right) {
    int sum = arr[left] + arr[right];
    if (sum == target) {
        // pair found
    } else if (sum < target) {
        left++;
    } else {
        right--;
    }
}
```

---

### 2. Same Direction (Sliding Window)
**Use case:** Subarray/substring problems with min/max length or sum.

```java
int left = 0, sum = 0;
for (int right = 0; right < arr.length; right++) {
    sum += arr[right];
    while (sum > target) {
        sum -= arr[left++];
    }
}
```

---

### 3. Fast and Slow Pointers
**Use case:** Cycle detection, remove duplicates, linked list problems.

```java
int slow = 0;
for (int fast = 1; fast < nums.length; fast++) {
    if (nums[fast] != nums[slow]) {
        slow++;
        nums[slow] = nums[fast];
    }
}
return slow + 1;
```

---

### 4. Two Arrays/Strings Comparison
**Use case:** Merging, intersection, similarity check.

```java
int i = 0, j = 0;
while (i < arr1.length && j < arr2.length) {
    if (arr1[i] == arr2[j]) {
        // do something
        i++; j++;
    } else if (arr1[i] < arr2[j]) {
        i++;
    } else {
        j++;
    }
}
```

---

### 5. Partition Around Pivot / In-Place Swaps
**Use case:** Sorting, partitioning, Dutch National Flag, QuickSort.

```java
int low = 0, mid = 0, high = arr.length - 1;
while (mid <= high) {
    if (arr[mid] == 0) {
        swap(arr, low++, mid++);
    } else if (arr[mid] == 1) {
        mid++;
    } else {
        swap(arr, mid, high--);
    }
}
```

---

## 🧠 Master Tips & Techniques

- **TIP 1: Sort If Not Sorted**  
  For problems like 2Sum/3Sum, sorting first often enables Two Pointers.

- **TIP 2: Know When to Shrink**  
  In sliding window, always ask: _When should I shrink the window?_ (e.g., when sum/condition is violated).

- **TIP 3: Avoid Unnecessary Loops**  
  Two Pointers often turn nested loops into a single pass.

- **TIP 4: Edge Cases**  
  Handle empty arrays, all identical elements, or cases with no answer.

- **TIP 5: Understand the Output**  
  Do you need the count, indices, or actual elements? Adjust logic accordingly.

- **TIP 6: Linked List Caution**  
  For singly linked lists, Two Pointers can help find cycle, midpoint, or nth-from-end node.

- **TIP 7: Multiple Pointers**
  Sometimes, more than two pointers (e.g., 3Sum, 4Sum) are used by fixing one and using Two Pointers for the rest.

---

## 🛠️ Common Pitfalls

- **Unsorted Input:**  
  Two Pointers often require sorted input for correctness.

- **Pointer Overlap:**  
  Make sure pointers don’t cross or miss edge conditions (e.g., left < right, or left <= right).

- **Infinite Loops:**  
  Always increment/decrement pointers under all conditions.

- **Forgetting In-Place Requirements:**  
  Use pointers wisely to avoid extra space.

---
