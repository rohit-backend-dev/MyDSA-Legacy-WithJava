268. Missing Number
- Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.
## 🔴 1. **Brute Force Approach**

### ➤ **Time Complexity:** O(n²)

### ➤ **Space Complexity:** O(1)

### ✅ **Idea:**

Loop through all numbers from `0` to `n`, and for each number, check if it's present in the array by scanning the entire array.

### 🔍 Why it's called brute force?

Because you’re checking every possible number (from 0 to n) manually in the array. This is inefficient for large inputs.

### 💡 Example:

For input: `nums = [3, 0, 1]`
We’ll check:

* Is 0 in array? Yes
* Is 1 in array? Yes
* Is 2 in array? ❌ No → That's our missing number

### ✅ Code:

```java
class Solution {
    public int missingNumber(int[] nums) {
        int n = nums.length;
        for (int i = 0; i <= n; i++) {
            boolean found = false;
            for (int j = 0; j < n; j++) {
                if (nums[j] == i) {
                    found = true;
                    break;
                }
            }
            if (!found) return i;
        }
        return -1;
    }
}
```

---

## 🟡 2. **Better Approach using HashSet**

### ➤ **Time Complexity:** O(n)

### ➤ **Space Complexity:** O(n)

### ✅ **Idea:**

Store all elements of the array into a `HashSet`. Then check from `0` to `n` which number is missing.

### 🔍 Why is it better?

Because `HashSet` provides **O(1)** lookup time. So, instead of scanning the entire array for every number, we just check if it's in the set.

### 💡 Example:

Set = {0, 1, 3}
Check from 0 to 3

* 0 ✅
* 1 ✅
* 2 ❌ → missing

### ✅ Code:

```java
import java.util.HashSet;

class Solution {
    public int missingNumber(int[] nums) {
        HashSet<Integer> set = new HashSet<>();
        for (int num : nums) {
            set.add(num);
        }

        for (int i = 0; i <= nums.length; i++) {
            if (!set.contains(i)) {
                return i;
            }
        }
        return -1;
    }
}
```

---

## 🟢 3. **Optimal Approach using Sum Formula**

### ➤ **Time Complexity:** O(n)

### ➤ **Space Complexity:** O(1)

### ✅ **Idea:**

Use the formula:

$$
\text{Sum of first n numbers} = \frac{n(n+1)}{2}
$$

Subtract the **sum of array elements** from this total — the difference is the missing number.

### 💡 Intuition:

* You know the total of numbers from 0 to n.
* Subtract the actual sum of elements you have.
* The missing number is the difference.

### 💡 Example:

Array: `[3, 0, 1]`
Length = 3
Expected sum = 3×(3+1)/2 = 6
Actual sum = 3 + 0 + 1 = 4
Missing = 6 - 4 = **2**

### ✅ Code:

```java
class Solution {
    public int missingNumber(int[] nums) {
        int n = nums.length;
        int totalSum = n * (n + 1) / 2;

        int actualSum = 0;
        for (int num : nums) {
            actualSum += num;
        }

        return totalSum - actualSum;
    }
}
```

---

## 💥 BONUS: XOR-Based Optimal Solution

### ➤ **Time Complexity:** O(n)

### ➤ **Space Complexity:** O(1)

### ✅ **Idea:**

XOR has special properties:

Sure! Here's a **simple version** of these XOR rules with number examples — just like you asked (e.g., `2 ^ 2 = 0` style):

---

### ✅ `a ^ a = 0`

Same number XORed with itself gives 0.

* `2 ^ 2 = 0`
* `5 ^ 5 = 0`
* `10 ^ 10 = 0`

---

### ✅ `a ^ 0 = a`

Any number XORed with 0 stays the same.

* `2 ^ 0 = 2`
* `7 ^ 0 = 7`
* `15 ^ 0 = 15`

---

### ✅ `a ^ b ^ a = b`

XOR same number twice cancels it out.

* `4 ^ 6 ^ 4 = 6`
* `9 ^ 3 ^ 9 = 3`
* `7 ^ 2 ^ 7 = 2`

If you XOR all elements from `0` to `n`, and then XOR all numbers in the array — the duplicate elements cancel out, and you are left with the missing number.

### 💡 Example:

nums = `[3, 0, 1]`, n = 3
0 ^ 1 ^ 2 ^ 3 = **0^1^2^3**
0 ^ 1 ^ 3 = **0^1^3**

Final XOR:
(0^1^2^3) ^ (0^1^3) = **2**

### ✅ Code:

```java
class Solution {
    public int missingNumber(int[] nums) {
        int xor = 0;
        int n = nums.length;

        for (int i = 0; i <= n; i++) {
            xor ^= i;       // XOR of all numbers from 0 to n
        }

        for (int num : nums) {
            xor ^= num;     // XOR of all numbers in array
        }

        return xor;
    }
}
```

---

## ✅ Summary Table

| Approach          | Time  | Space | Notes                          |
| ----------------- | ----- | ----- | ------------------------------ |
| Brute Force       | O(n²) | O(1)  | Inefficient, just for learning |
| HashSet / HashMap | O(n)  | O(n)  | Simple & effective             |
| Sum Formula       | O(n)  | O(1)  | Best & cleanest                |
| XOR               | O(n)  | O(1)  | Bit-manipulation trick         |

---
