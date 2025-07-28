# Make Matrix Beautiful

---

## 🔧 **Problem Statement**

Given an `n x n` matrix, you can increment **any cell** by `1` any number of times.  
**Goal:** Make all **row sums** and **column sums** equal using the **minimum number of operations**.

---

## 🚦 **Why is this Problem Interesting?**

- **Constraints:** Only increments (no decrements) are allowed.
- **Objective:** Equalize all row and column sums with the fewest total increments.
- **Applications:**  
  - Magic square transformations
  - Load balancing in grids
  - Puzzle/game design
  - Matrix normalization for data processing

---

## 🏗️ **Approaches**

### 1. Brute Force (For Small Matrices)

#### **Idea**

- Find the **maximum** among all row and column sums (`maxSum`).
- Increment cells so all rows/columns reach `maxSum`.
- For each row, compute how much it lacks compared to `maxSum`. The sum of these deficits is the answer.

#### **Why does this work?**

- Since you can only increment, **no row or column can ever exceed maxSum**.
- Any increment to a cell affects both its row and column, but incrementing any cell in a row/column that already meets `maxSum` would be wasteful.
- Therefore, the minimal total increments required is simply the sum of the deficits of each row/column to `maxSum`.

#### **Java Implementation**

```java
public class MakeMatrixBeautifulBruteForce {
    public static int findMinOperationsBrute(int[][] mat) {
        int n = mat.length;
        int[] rowSum = new int[n];
        int[] colSum = new int[n];

        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++) {
                rowSum[i] += mat[i][j];
                colSum[j] += mat[i][j];
            }

        int maxSum = 0;
        for (int i = 0; i < n; i++) {
            maxSum = Math.max(maxSum, rowSum[i]);
            maxSum = Math.max(maxSum, colSum[i]);
        }

        int totalOperations = 0;
        for (int i = 0; i < n; i++) {
            totalOperations += maxSum - rowSum[i];
        }

        return totalOperations;
    }
}
```

#### **Dry Run Example**

Input:
```
1 2
3 4
```
- Row sums: [3, 7]
- Col sums: [4, 6]
- maxSum = 7

Operations needed:
- Row 0: 7 - 3 = 4
- Row 1: 7 - 7 = 0  
**Total = 4**

---

### 2. **Intersection Greedy Approach (Optimal for All n)**

#### **Key Insight: Why Intersection?**

Every increment at cell `(i, j)` **contributes simultaneously** to both its row and its column.  
So, **always increment the intersection** of the row and column that are furthest behind.

- If you increment only row-wise or column-wise, you may end up "overfilling" columns or rows unnecessarily.
- At each step, to be optimal, you want to add as much as possible without exceeding `maxSum` in either the current row or column.

#### **What is the "Intersection"?**

- In a matrix, cell `(i, j)` is at the intersection of row `i` and column `j`.
- By incrementing this cell, you increase both `rowSum[i]` and `colSum[j]` by 1.
- The trick is to always pick the intersection where **both the row and column are lagging behind the target**.

#### **Algorithm**

1. **Calculate all row and column sums.**
2. Find `maxSum` = maximum among all row and column sums.
3. Use two pointers `i`, `j` for the current row and column.
4. At each step:
   - Compute how much is needed for the current row and column to reach `maxSum`.
   - Let `diff = min(maxSum - rowSum[i], maxSum - colSum[j])`
   - Increment `mat[i][j]` by `diff`.
   - Update `rowSum[i]` and `colSum[j]` by `diff`.
   - Add `diff` to the total operation count.
   - If `rowSum[i]` reaches `maxSum`, move to the next row (`i++`).
   - If `colSum[j]` reaches `maxSum`, move to the next column (`j++`).
5. Repeat until all rows and columns reach `maxSum`.

#### **Why is this Optimal?**

- Every increment at `(i, j)` reduces the deficit in both row `i` and column `j` **simultaneously**.
- At every step, you close the smallest gap (either the row or col), so there's no wasted increment.
- You will never "overfill" any row or column, and you will never miss an opportunity to fill both at once.

#### **Java Implementation**

```java
public class MakeMatrixBeautifulOptimal {
    public static int findMinOperationsOptimal(int[][] mat) {
        int n = mat.length;
        int[] rowSum = new int[n];
        int[] colSum = new int[n];
        int maxSum = 0;

        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++) {
                rowSum[i] += mat[i][j];
                colSum[j] += mat[i][j];
            }

        for (int i = 0; i < n; i++) {
            maxSum = Math.max(maxSum, rowSum[i]);
            maxSum = Math.max(maxSum, colSum[i]);
        }

        int i = 0, j = 0, operations = 0;
        while (i < n && j < n) {
            int diff = Math.min(maxSum - rowSum[i], maxSum - colSum[j]);
            mat[i][j] += diff;
            rowSum[i] += diff;
            colSum[j] += diff;
            operations += diff;

            if (rowSum[i] == maxSum) i++;
            if (colSum[j] == maxSum) j++;
        }

        return operations;
    }
}
```
---

## 🧠 **Step-by-Step 3x3 Example: Intersection Approach**

### **Input Matrix**

```
1 2 3
4 2 3
3 2 1
```

#### **Step 1: Compute Row and Column Sums**

| Row | Sum | Col | Sum |
|-----|-----|-----|-----|
|  0  |  6  |  0  | 8   |
|  1  |  9  |  1  | 6   |
|  2  |  6  |  2  | 7   |

- maxSum = 9 (from Row 1)

#### **Step 2: Matrix Total**

- Total = 1+2+3+4+2+3+3+2+1 = 21

#### **Step 3: Intersection Steps**

Let's walk through the greedy intersection approach step by step:

1. **Initial Sums:**  
   RowSum = [6, 9, 6], ColSum = [8, 6, 7], maxSum = 9  
   Operations = 0

2. **Step (0,0):**  
   - rowSum[0]=6, colSum[0]=8
   - `diff = min(9-6, 9-8) = min(3,1) = 1`
   - Add 1 to mat[0][0] → now mat[0][0]=2
   - Update: rowSum[0]=7, colSum[0]=9, ops=1

3. **Step (0,1):**  
   - rowSum[0]=7, colSum[1]=6
   - `diff = min(9-7, 9-6) = min(2,3)=2`
   - Add 2 to mat[0][1] → now mat[0][1]=4
   - Update: rowSum[0]=9, colSum[1]=8, ops=3

4. **Step (1,1):**  
   - rowSum[1]=9, colSum[1]=8
   - Since rowSum[1]=maxSum, move to row 2.

5. **Step (2,1):**  
   - rowSum[2]=6, colSum[1]=8
   - `diff = min(9-6, 9-8) = min(3,1)=1`
   - Add 1 to mat[2][1] → now mat[2][1]=3
   - Update: rowSum[2]=7, colSum[1]=9, ops=4

6. **Step (2,2):**  
   - rowSum[2]=7, colSum[2]=7
   - `diff = min(9-7, 9-7)=2`
   - Add 2 to mat[2][2] → now mat[2][2]=3
   - Update: rowSum[2]=9, colSum[2]=9, ops=6

**Final matrix (one of many possible):**
```
2 4 3
4 2 3
3 3 3
```
Each row and column sums to 9.

---

## 🔍 **Visualizing the Intersection Approach**

### **Diagram Representation**

Suppose at any step:

- Row i needs `gapRow = maxSum - rowSum[i]`
- Column j needs `gapCol = maxSum - colSum[j]`

At cell `(i, j)`, you can add `diff = min(gapRow, gapCol)`:

```
[Before]
Row i: .... gapRow left
Col j: .... gapCol left

[Action]
mat[i][j] += diff

[After]
Row i: gapRow -= diff
Col j: gapCol -= diff

If gapRow == 0: move to next row
If gapCol == 0: move to next column
```

- **Key:** No increment is wasted; every increment brings both a row and a column closer to the target.

---

## 🏁 **Summary Table**

| Approach   | Time       | Space | Description                       | Formula                             |
|------------|------------|-------|-----------------------------------|-------------------------------------|
| Brute      | O(n²)      | O(n)  | Fill each row to maxSum           | sum(maxSum - rowSum[i])             |
| Greedy     | O(n²)      | O(n)  | Use intersection of row & col     | n × maxSum - total(matrix)          |
| One-Liner  | O(n²)      | O(1)  | Compute maxSum and total sum      | n × maxSum - total(matrix)          |

---
