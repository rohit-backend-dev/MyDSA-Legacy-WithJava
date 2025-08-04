## ✅ Problem: Maximum Sum Rectangle in a 2D Matrix

You’re given a matrix (2D array) of numbers — positive or negative.

Your task is to **find the rectangle inside the matrix** (can be any size, anywhere) that has the **maximum sum of all its numbers**.

Example:

```text
Matrix:
  1   2  -1
 -3   4   5
  2  -6   3

→ Best rectangle (bold values):
  1   2  -1
 -3  [4   5]
  2 [-6   3]

→ Best sum = 4 + 5 + (-6) + 3 = **6**
```

So, find that submatrix and return its total sum — the **highest possible** among all options.

---

## ✅ Java Code

```java
class Solution {
    public int maxRectSum(int[][] mat) {
        int n = mat.length;
        if (n == 0) return 0;
        int m = mat[0].length;
        int maxSum = Integer.MIN_VALUE;

        for (int left = 0; left < m; left++) {
            int[] temp = new int[n];

            for (int right = left; right < m; right++) {
                for (int row = 0; row < n; row++) {
                    temp[row] += mat[row][right];
                }

                int currMax = kadane(temp);
                maxSum = Math.max(maxSum, currMax);
            }
        }

        return maxSum;
    }

    private int kadane(int[] arr) {
        int max1 = arr[0];
        int res = arr[0];

        for (int i = 1; i < arr.length; i++) {
            max1 = Math.max(arr[i], max1 + arr[i]);
            res = Math.max(res, max1);
        }

        return res;
    }
}
```

---

## 📘 Detailed Explanation

### 🧠 Idea Behind the Solution

We use a smart trick:
Turn the 2D matrix into multiple 1D problems and solve each one using **Kadane’s algorithm** (used to find max sum subarray in 1D).

---

### 🔁 How It Works

1. **Pick two columns** (`left` and `right`).
2. **Collapse the matrix** between those columns into a 1D array (`temp[]`) of row sums.
3. **Apply Kadane’s** on that `temp[]` to find best rows.
4. Do this for every column pair and update the global maximum.

---

### 📐 Why `temp[]` Works?

Each index `i` in `temp[]` represents the sum of elements in row `i` between the `left` and `right` columns.

So applying Kadane’s on `temp[]` tells us:

> "Among all row blocks, which gives the best rectangle sum between column `left` and `right`?"

---

### ⏱ Time Complexity

```
O(m² * n)
```

Where:

* `m` = number of columns
* `n` = number of rows
  This is efficient and works well for normal input sizes.

---

### 🧪 Example

Input:

```java
mat = {
  {1, 2, -1, -4, -20},
  {-8, -3, 4, 2, 1},
  {3, 8, 10, 1, 3},
  {-4, -1, 1, 7, -6}
}
```

Output:

```
29
```

That’s the sum of the best rectangle:

```
[4, 2, 1]
[10, 1, 3]
[1, 7, -6]
```

