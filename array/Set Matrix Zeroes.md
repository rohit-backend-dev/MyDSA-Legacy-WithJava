# Set Matrix Zeroes

## Problem Statement

Given an `m x n` matrix, if an element is 0, set its entire row and column to 0. You must do it in place.

---

## Brute Force (Marker -1)

**Idea:**  
When a 0 is found, mark all elements in its row and column as -1 (unless they're already 0 or -1). In a second pass, convert all -1 cells to 0.

**Note:**  
This only works if the matrix does not contain negative numbers. If negatives exist, use a marker like -999999.

### Java Code

```java
public class Solution {
    public void setZeroes(int[][] matrix) {
        int m = matrix.length;
        int n = matrix[0].length;

        // First pass: mark cells as -1 where needed
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (matrix[i][j] == 0) {
                    // Mark row
                    for (int col = 0; col < n; col++) {
                        if (matrix[i][col] != 0 && matrix[i][col] != -1) {
                            matrix[i][col] = -1;
                        }
                    }
                    // Mark column
                    for (int row = 0; row < m; row++) {
                        if (matrix[row][j] != 0 && matrix[row][j] != -1) {
                            matrix[row][j] = -1;
                        }
                    }
                }
            }
        }

        // Second pass: convert all -1 to 0
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (matrix[i][j] == -1) {
                    matrix[i][j] = 0;
                }
            }
        }
    }
}
```

**Time Complexity:**  
O(m × n × (m + n)) — Multiple passes per zero found.

**Space Complexity:**  
O(1) — In-place (only uses marker).

---

## Better Solution (Using Extra Space)

**Idea:**  
Track which rows and columns need to be zeroed using separate arrays (or sets).  
First, traverse and note all rows/columns containing zero.  
Then, in a second pass, set cells to zero if their row or column is marked.

### Java Code (Using Arrays)

```java
public class Solution {
    public void setZeroes(int[][] matrix) {
        int m = matrix.length;
        int n = matrix[0].length;

        boolean[] row = new boolean[m];
        boolean[] col = new boolean[n];

        // Step 1: Mark the rows and cols that should be zero
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (matrix[i][j] == 0) {
                    row[i] = true;
                    col[j] = true;
                }
            }
        }

        // Step 2: Set cells to 0 based on marked rows and cols
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (row[i] || col[j]) {
                    matrix[i][j] = 0;
                }
            }
        }
    }
}
```

**Alternate using HashSets** (for clarity, not efficiency):

```java
import java.util.*;

public class Solution {
    public void setZeroes(int[][] matrix) {
        int m = matrix.length, n = matrix[0].length;
        Set<Integer> zeroRows = new HashSet<>();
        Set<Integer> zeroCols = new HashSet<>();

        // Find all rows and columns with a 0
        for (int i = 0; i < m; i++)
            for (int j = 0; j < n; j++)
                if (matrix[i][j] == 0) {
                    zeroRows.add(i);
                    zeroCols.add(j);
                }

        // Set affected cells to 0
        for (int i = 0; i < m; i++)
            for (int j = 0; j < n; j++)
                if (zeroRows.contains(i) || zeroCols.contains(j))
                    matrix[i][j] = 0;
    }
}
```

**Time Complexity:**  
O(m × n)

**Space Complexity:**  
O(m + n) — Arrays/sets for rows and columns.

---

## Optimal Solution (O(1) Space)

**Idea:**  
Use the first row and first column of the matrix as marker arrays to store zero info, plus two booleans to track if the first row and/or column should be zeroed.

### Java Code

```java
public class Solution {
    public void setZeroes(int[][] matrix) {
        int m = matrix.length, n = matrix[0].length;

        // Flags to remember if the first row and column need to be zeroed
        boolean firstRow = false, firstCol = false;

        // Step 1: Check if any cell in the first column is 0
        // If yes, we need to zero out the entire first column later
        for (int i = 0; i < m; i++) {
            if (matrix[i][0] == 0) {
                firstCol = true;
                break;
            }
        }

        // Step 2: Check if any cell in the first row is 0
        // If yes, we need to zero out the entire first row later
        for (int j = 0; j < n; j++) {
            if (matrix[0][j] == 0) {
                firstRow = true;
                break;
            }
        }

        // Step 3: Use first row and column to mark which rows and columns need to be zeroed
        // For each zero found at (i, j), mark its row and column at matrix[i][0] and matrix[0][j]
        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                if (matrix[i][j] == 0) {
                    matrix[i][0] = 0;  // Mark row i
                    matrix[0][j] = 0;  // Mark column j
                }
            }
        }

        // Step 4: Use the markers to set cells to 0
        // If either the row or column is marked, set cell (i, j) to 0
        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                if (matrix[i][0] == 0 || matrix[0][j] == 0) {
                    matrix[i][j] = 0;
                }
            }
        }

        // Step 5: If firstRow flag is true, zero the entire first row
        if (firstRow) {
            for (int j = 0; j < n; j++) {
                matrix[0][j] = 0;
            }
        }

        // Step 6: If firstCol flag is true, zero the entire first column
        if (firstCol) {
            for (int i = 0; i < m; i++) {
                matrix[i][0] = 0;
            }
        }
    }
}

```

**Time Complexity:**  
O(m × n)

**Space Complexity:**  
O(1) — No extra arrays, just booleans.

---

## Complexity Comparison

| Approach              | Time Complexity            | Space Complexity | Notes                          |
|-----------------------|---------------------------|------------------|--------------------------------|
| Brute-force (-1)      | O(m × n × (m+n))          | O(1)             | Slow, multiple passes          |
| Better (extra arrays) | O(m × n)                  | O(m + n)         | Simple, extra storage needed   |
| Optimal (in-place)    | O(m × n)                  | O(1)             | Best for interviews            |

---

## Dry Run Example

Initial matrix:
```
[
  [1, 2, 0],
  [4, 5, 6],
  [7, 0, 9]
]
```

Let's walk through the **Optimal Solution**:

1. **Check first row/col for zero:**  
   - First row has a 0 at index 2 → `firstRow = true`
   - First column has no zero → `firstCol = false`

2. **Mark zeros using first row/col (excluding first row/col):**
   - At (2,1) value is 0: mark matrix[2][0] = 0 and matrix[0][1] = 0

   Matrix now:
   ```
   [
     [1, 0, 0],
     [4, 5, 6],
     [0, 0, 9]
   ]
   ```

3. **Set zeroes based on markers (excluding first row/col):**
   - At (1,1): matrix[1][0] = 4, matrix[0][1] = 0 ⇒ set matrix[1][1] = 0
   - At (1,2): matrix[1][0] = 4, matrix[0][2] = 0 ⇒ set matrix[1][2] = 0
   - At (2,0): already 0
   - At (2,1): already 0
   - At (2,2): matrix[2][0] = 0 ⇒ set matrix[2][2] = 0

   Matrix now:
   ```
   [
     [1, 0, 0],
     [4, 0, 0],
     [0, 0, 0]
   ]
   ```

4. **Zero first row if needed:**
   - Yes, so set all of matrix[0][j] to 0

   ```
   [
     [0, 0, 0],
     [4, 0, 0],
     [0, 0, 0]
   ]
   ```

5. **Zero first column if needed:**
   - No (firstCol is false)

Final Output:
```
[
  [0, 0, 0],
  [4, 0, 0],
  [0, 0, 0]
]
```

---
