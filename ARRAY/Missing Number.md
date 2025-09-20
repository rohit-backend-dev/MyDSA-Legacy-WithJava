# 📘 Missing Number (LeetCode 268) — Solutions & Explanations

We are given an array `nums` containing `n` distinct numbers taken from range `[0, n]`. One number is missing.
We need to find that missing number.

---

## ✅ 1. Math (Sum Formula) Approach

### 🔹 Idea

* The sum of first `n` natural numbers (from `0` to `n`) is:

  $$
  \text{expectedSum} = \frac{n \cdot (n+1)}{2}
  $$
* Compute the **actual sum** of elements in `nums`.
* The difference between expected and actual gives the missing number.

### 🔹 Code

```java
class Solution {
    public int missingNumber(int[] nums) {
        int n = nums.length;

        // Expected sum of 0..n
        int expectedSum = n * (n + 1) / 2;

        // Actual sum of array
        int actualSum = 0;
        for (int num : nums) {
            actualSum += num;
        }

        // Missing number is the difference
        return expectedSum - actualSum;
    }
}
```

### 🔹 Complexity

* **Time:** O(n) (loop once to sum).
* **Space:** O(1) (no extra space).

---

## ✅ 2. XOR Method

### 🔹 Idea

* Use property of XOR:

  * `a ^ a = 0`
  * `a ^ 0 = a`
* XOR all numbers from `0..n` with all elements in `nums`.
* Numbers that appear in both cancel out, leaving the missing number.

### 🔹 Code

```java
class Solution {
    public int missingNumber(int[] nums) {
        int n = nums.length;
        int xor = 0;

        // XOR indices from 0..n
        for (int i = 0; i <= n; i++) {
            xor ^= i;
        }

        // XOR all array elements
        for (int num : nums) {
            xor ^= num;
        }

        return xor; // Missing number
    }
}
```

### 🔹 Complexity

* **Time:** O(n) (two loops, still linear).
* **Space:** O(1).

