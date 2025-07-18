# Maximum LCM of Any Three Numbers ≤ N (Optimized Explanation + Code)

## Problem Explanation with Optimized Approach

**Problem Statement:**  
Given a positive integer `n`, select any three positive integers less than or equal to `n` such that their Least Common Multiple (LCM) is maximized.  
Find the maximum possible LCM and briefly explain why your solution works.

**Example:**  
- If `n = 9`, the maximum LCM is `504` (from triplet {7, 8, 9}).
- If `n = 7`, the maximum LCM is `210` (from triplet {5, 6, 7}).

---

## Important Observations

- **LCM increases with large numbers, especially when they are pairwise coprime (minimal common divisibility):**  
  The largest three numbers close to `n` will tend to give the largest LCM because LCM depends on the maximum spread of numbers and their prime factors.

- **GCD (Greatest Common Divisor) impacts LCM:**  
  If numbers have common divisors, their LCM reduces because:
  ```
  LCM(a, b, c) = smallest number divisible by a, b, and c
               = LCM(LCM(a, b), c)
  ```
  So, consecutive numbers often give better results, especially when they include primes or coprime numbers.

- **Formula Insight:**  
  For large `n`, generally, the LCM of `{n, n-1, n-2}` or `{n, n-1, n-3}` or `{n-1, n-2, n-3}` gives the maximum result.

---

## Examples Explained

**Example 1:**  
n = 9  
- Triplet `{7, 8, 9}`:  
  - LCM(7, 8) = 56  
  - LCM(56, 9) = 504  
  ✅ Highest LCM = 504

  Other triplets like `{9, 8, 6}` or `{9, 7, 6}` result in lower LCM because they miss out on numbers with large spread or relatively prime values.

**Example 2:**  
n = 7  
- Triplet `{5, 6, 7}`:  
  - LCM(5, 6) = 30  
  - LCM(30, 7) = 210  
  ✅ Highest LCM = 210

---

## Solution 1: Naive Approach

### Idea
- Brute-force all possible triplets `(a, b, c)` where `1 ≤ a < b < c ≤ n`.
- For each triplet, compute their LCM.
- Track the maximum LCM found.

### Code (Java-style pseudocode)
```java
long maxLCM = 0;
for (int a = 1; a <= n; a++) {
    for (int b = a + 1; b <= n; b++) {
        for (int c = b + 1; c <= n; c++) {
            long currentLCM = lcmOfThree(a, b, c);
            if (currentLCM > maxLCM) maxLCM = currentLCM;
        }
    }
}
return maxLCM;
```
*`lcmOfThree(a, b, c)` computes LCM using pairwise LCMs.*

### Complexity
- **Time:** O(n³ · log n) (very slow for large `n`)
- **Space:** O(1) (only storing max value)

### Use Case
- Only practical for small values of `n` (say, `n ≤ 30`).

---

## Solution 2: Optimized Approach (Using Mathematical Formula)

### Key Observations
- LCM increases with large numbers, especially when they are pairwise coprime (minimal common divisibility).
- For most values of `n`, the largest numbers close to `n` (and coprime) will yield the largest LCM.

### Formula
- For `n ≤ 2`: answer is `n`.
- For `n = 3`: answer is `6` (triplet {1, 2, 3}).
- For **odd `n`**:  
  Maximum LCM is `LCM(n, n-1, n-2)`.
- For **even `n`**:  
  Maximum LCM is `max(LCM(n, n-1, n-3), LCM(n-1, n-2, n-3))`.

#### Why?
- **Odd n:** The top three numbers are pairwise coprime, maximizing LCM.
- **Even n:** Consecutive numbers may share factors (2 or 3). Skipping one (use `n-3` instead of `n-2`) often yields a higher LCM.

### Code (Java)
```java
class Solution{
public static long gcd(long a, long b) {
    while (b != 0) {
        long temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

public static long lcm(long a, long b) {
    return a * (b / gcd(a, b));
}

public static long lcmOfThree(long a, long b, long c) {
    return lcm(lcm(a, b), c);
}

public static long lcmTriplets(int n) {
    if (n == 1) return 1;
    if (n == 2) return 2;
    if (n == 3) return 6;
    if (n % 2 != 0) {
        return lcmOfThree(n, n-1, n-2);
    } else {
        return Math.max(
            lcmOfThree(n, n-1, n-3),
            lcmOfThree(n-1, n-2, n-3)
        );
    }
}
```

### Complexity
- **Time:** O(log n) per GCD call (very fast, handles `n` up to 10⁶+)
- **Space:** O(1)

---

## Summary Table

| Approach      | Time Complexity         | Works for Large n? | Correctness | Explanation                                               |
|---------------|------------------------|--------------------|-------------|-----------------------------------------------------------|
| **Naive**     | O(n³ · log n)          | ❌ No              | ✅ Yes      | Checks all triplets, but too slow for large n             |
| **Optimized** | O(log n) per GCD call  | ✅ Yes             | ✅ Yes      | Uses mathematical insight and coprimality to quickly compute max LCM |
---
