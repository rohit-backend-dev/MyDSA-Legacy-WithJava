# 📘 1614. Maximum Nesting Depth of the Parentheses 

---

## 🔹 Solution 1: Counter-Based Approach (Optimal)

### Idea

* Instead of using a stack, maintain a **depth counter**.
* Increase `depth` on `'('`, decrease on `')'`.
* Track the maximum value of `depth`.

### Code

```java
class Solution {
    public int maxDepth(String s) {
        int depth = 0, maxDepth = 0;
        for (char ch : s.toCharArray()) {
            if (ch == '(') {
                depth++;
                maxDepth = Math.max(maxDepth, depth);
            } else if (ch == ')') {
                depth--;
            }
        }
        return maxDepth;
    }
}
```

### Complexity

* **Time:** O(n) → single pass
* **Space:** O(1) → just counters

### Notes

* This is the **fastest and most memory-efficient solution**.
* Usually runs in **0 ms** and beats \~100% of submissions.

---

## 🔹 Solution 2: Stack-Based Approach (More Intuitive)

### Idea

* Use a **stack** to simulate parentheses nesting.
* Push `(` onto stack, pop when encountering `)`.
* The **maximum stack size** = maximum nesting depth.

### Code

```java
import java.util.Stack;

class Solution {
    public int maxDepth(String s) {
        Stack<Character> stack = new Stack<>();
        int maxDepth = 0;

        for (char ch : s.toCharArray()) {
            if (ch == '(') {
                stack.push(ch);
                maxDepth = Math.max(maxDepth, stack.size());
            } else if (ch == ')') {
                stack.pop();
            }
        }

        return maxDepth;
    }
}
```

### Complexity

* **Time:** O(n)
* **Space:** O(n) (in worst case, stack stores all `(`)

### Notes

* Easier to visualize for beginners.
* But slower (extra push/pop operations).
* Typically runs in **1 ms**, \~25–30% beats on LeetCode.

---

## 🔹 Comparison

| Approach | Time | Space | Speed on LeetCode | Use Case                         |
| -------- | ---- | ----- | ----------------- | -------------------------------- |
| Counter  | O(n) | O(1)  | 🚀 0 ms (\~100%)  | Best for interviews & production |
| Stack    | O(n) | O(n)  | 🐢 1 ms (\~25%)   | Best for teaching & clarity      |

---

👉 **Takeaway**:

* Use **Counter Method** in interviews & submissions.
* Mention the **Stack Method** as an alternative if asked for different approaches.
