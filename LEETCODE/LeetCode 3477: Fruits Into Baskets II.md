 **LeetCode 3477: Fruits Into Baskets II** in **Java**, using a **greedy + two-pointer** approach.

---

### 🔍 **Problem Understanding**

For each fruit from **left to right**, we must place it in the **leftmost basket** that:

* Has **not been used yet**, and
* Has **capacity ≥ fruit quantity**

If no such basket exists, the fruit is **unplaced**.

---

### ✅ **Approach**

1. Iterate through each fruit from left to right.
2. For each fruit, scan baskets from left to right.
3. If you find an **unused basket** with **sufficient capacity**, assign the fruit and mark that basket as used.
4. If no such basket is found, increment the **unplaced count**.
5. Return the count of unplaced fruits.

---

### ✅ Java Code

```java
public class Solution {
    public int unplacedFruits(int[] fruits, int[] baskets) {
        int n = fruits.length;
        boolean[] used = new boolean[n];  // Track used baskets
        int unplaced = 0;

        for (int i = 0; i < n; i++) {
            boolean placed = false;
            for (int j = 0; j < n; j++) {
                if (!used[j] && baskets[j] >= fruits[i]) {
                    used[j] = true;  // Mark this basket as used
                    placed = true;
                    break;
                }
            }
            if (!placed) {
                unplaced++;
            }
        }

        return unplaced;
    }

    // Example usage
    public static void main(String[] args) {
        Solution sol = new Solution();
        System.out.println(sol.unplacedFruits(new int[]{4, 2, 5}, new int[]{3, 5, 4})); // Output: 1
        System.out.println(sol.unplacedFruits(new int[]{3, 6, 1}, new int[]{6, 4, 7})); // Output: 0
    }
}
```

---

### 🧠 Time & Space Complexity

* **Time Complexity:** `O(n^2)` in the worst case (for each fruit, we may scan all baskets).
* **Space Complexity:** `O(n)` for the `used[]` array.

---
