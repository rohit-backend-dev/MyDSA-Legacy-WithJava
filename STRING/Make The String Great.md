## 🧩 Problem Understanding

We’re given a string `s` consisting of **uppercase and lowercase English letters**.

We must **remove all “bad pairs”** of adjacent characters until none remain.

---

### ❌ What is a "bad pair"?

Two **adjacent characters** are bad if:

* They are the **same letter**, but **different cases** (one lowercase, one uppercase).

That means:

* `'a'` and `'A'` → bad pair
* `'B'` and `'b'` → bad pair

When such a pair appears, we **remove both characters**.
We repeat this process until there are no bad pairs left.

---

### ✅ A “good string” means:

No two adjacent characters form a bad pair.

---

### 🧠 Example 1

**Input:**

```
s = "leEeetcode"
```

**Process:**

```
leEeetcode
 ↑↑
Remove 'eE' → "leetcode"
```

No more bad pairs → ✅ Done.

**Output:** `"leetcode"`

---

## 🧮 ASCII Trick

In ASCII, the difference between lowercase and uppercase of the same letter = **32**
(e.g. `'a' (97)` − `'A' (65)` = 32)

So, if
`Math.abs(s[i] - s[i+1]) == 32`,
then `s[i]` and `s[i+1]` are a **bad pair**.

---

## 🥇 **Solution 1: Stack Approach (Most Common & Efficient)**

### 🔧 Intuition:

We use a **stack** (or `StringBuilder` acting like a stack).
Iterate through each character:

* If the top of stack + current char form a bad pair → remove top.
* Else → push current char.

### ✅ Code:

```java
class Solution {
    public String makeGood(String s) {
        StringBuilder sb = new StringBuilder();

        for (char c : s.toCharArray()) {
            int len = sb.length();
            if (len > 0 && Math.abs(sb.charAt(len - 1) - c) == 32) {
                sb.deleteCharAt(len - 1); // remove bad pair
            } else {
                sb.append(c); // keep character
            }
        }

        return sb.toString();
    }
}
```

### ⏱️ Complexity:

* **Time:** O(n) (each character processed once)
* **Space:** O(n) (for the stack)

### 🧠 Example:

Input: `"leEeetcode"`
Output: `"leetcode"`

---

## 🥈 **Solution 2: In-place Simulation (Using Character Array)**

### 🔧 Intuition:

We can simulate a stack **within the same array** to save memory.
We maintain a pointer `top` to track the "top of stack".

### ✅ Code:

```java
class Solution {
    public String makeGood(String s) {
        char[] arr = s.toCharArray();
        int top = -1;

        for (char c : arr) {
            if (top >= 0 && Math.abs(arr[top] - c) == 32) {
                top--; // remove bad pair
            } else {
                arr[++top] = c; // push character
            }
        }

        return new String(arr, 0, top + 1);
    }
}
```

### ⏱️ Complexity:

* **Time:** O(n)
* **Space:** O(1) (in-place modification — most memory-efficient)
