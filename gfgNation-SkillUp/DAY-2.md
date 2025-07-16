# Counting Numbers ≤ N Having Exactly 9 Divisors

This document explains three efficient approaches to count how many numbers ≤ N have exactly 9 divisors, with code and usage scenarios.

---

## Mathematical Insight

A number has exactly 9 divisors if and only if:
- It is of the form **p⁸** (where p is a prime). Example: 2⁸ = 256.
- Or it is of the form **p² × q²** (where p and q are distinct primes). Example: 2² × 3² = 36.

Reason: For a number with prime factorization \( n = a^{x} \times b^{y} \), number of divisors is \( (x+1)\times(y+1) \). 9 = 8+1 or 3×3.

---

## 1. Brute Force Approach (O(N√N): For Small N)

Check every number up to N, count its divisors by iterating up to its square root.

```java
public class NineDivisorsBruteForce {
    public static int countNineDivisors(int n) {
        int count = 0;
        for (int i = 1; i <= n; i++) {
            int divisors = 0;
            for (int j = 1; j * j <= i; j++) {
                if (i % j == 0) {
                    if (j * j == i) divisors++;
                    else divisors += 2;
                }
            }
            if (divisors == 9) count++;
        }
        return count;
    }
    public static void main(String[] args) {
        System.out.println(countNineDivisors(100)); // Output: 2
    }
}
```
**When to Use:**  
- For small n (typically n ≤ 10⁴).
- For demonstration or learning.

---

## 2. Divisor Sieve Approach (O(N log N): For Moderate N)

Use a sieve to count divisors for all numbers up to n in one pass.

```java
public class NineDivisorsDivisorSieve {
    public static int countNineDivisors(int n) {
        int[] divCount = new int[n + 1];
        for (int i = 1; i <= n; i++) {
            for (int j = i; j <= n; j += i) {
                divCount[j]++;
            }
        }
        int count = 0;
        for (int i = 1; i <= n; i++) {
            if (divCount[i] == 9) count++;
        }
        return count;
    }
    public static void main(String[] args) {
        System.out.println(countNineDivisors(200)); // Output: 3
    }
}
```
**When to Use:**  
- For moderate n (up to ~10⁵).
- When divisor counts for all numbers are needed.

---

## 3. Optimized Mathematical (Sieve + Power Forms) Approach (O(√N log log N): For Large N)

Use Sieve of Eratosthenes up to √N to find primes, then count:
- Numbers of form p⁸ ≤ n.
- Numbers of form p² × q² ≤ n (for all distinct p < q).

```java
import java.util.*;

public class NineDivisorsOptimized {
    public static int countNineDivisors(int n) {
        int limit = (int)Math.sqrt(n) + 1;

        // Sieve of Eratosthenes
        boolean[] isPrime = new boolean[limit + 1];
        Arrays.fill(isPrime, true);
        isPrime[0] = isPrime[1] = false;
        for (int i = 2; i * i <= limit; i++) {
            if (isPrime[i]) {
                for (int j = i * i; j <= limit; j += i) isPrime[j] = false;
            }
        }
        List<Integer> primes = new ArrayList<>();
        for (int i = 2; i <= limit; i++) if (isPrime[i]) primes.add(i);

        int count = 0;
        // Count numbers of form p^8
        for (int p : primes) {
            long val = 1L * p * p * p * p * p * p * p * p;
            if (val <= n) count++;
            else break;
        }
        // Count numbers of form p^2 * q^2 (p < q)
        int size = primes.size();
        for (int i = 0; i < size; i++) {
            for (int j = i + 1; j < size; j++) {
                long val = 1L * primes.get(i) * primes.get(i) * primes.get(j) * primes.get(j);
                if (val <= n) count++;
                else break;
            }
        }
        return count;
    }
    public static void main(String[] args) {
        System.out.println(countNineDivisors(100)); // Output: 2
        System.out.println(countNineDivisors(200)); // Output: 3
    }
}
```
**When to Use:**  
- For large n (up to 10⁷ or higher).
- Fastest method for large inputs or coding contests/interviews.
---

# 🧮 Sieve of Eratosthenes: Find All Primes Up to N (With Style!)

---


## 🚀 What is the Sieve Approach?

The **Sieve of Eratosthenes** is a classic, super-efficient way to find _all prime numbers_ up to a given number `N`.

---

## 🔑 The Big Idea

1. **Make a List**: Write all numbers from `2` to `N`.
2. **Mark the Multiples**: For each number, cross out its multiples (they can't be primes!).
3. **What’s Left**: The numbers you didn’t cross out? Those are the primes!

---

## 📝 Step-by-Step Example (N = 30)

### 1️⃣ Start: Write the Numbers

```
2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30
```

---

### 2️⃣ Begin with 2 (the first prime)

- **Cross out all multiples of 2 (except 2 itself):**
  - 4, 6, 8, 10, ..., 30

```
2, 3, ~4~, 5, ~6~, 7, ~8~, 9, ~10~, 11, ~12~, 13, ~14~, 15, ~16~, 17, ~18~, 19, ~20~, 21, ~22~, 23, ~24~, 25, ~26~, 27, ~28~, 29, ~30~
```

---

### 3️⃣ Move to Next Uncrossed Number (3)

- **Cross out multiples of 3 (except 3):**
  - 6, 9, 12, ..., 30

```
2, 3, ~4~, 5, ~6~, 7, ~8~, ~9~, ~10~, 11, ~12~, 13, ~14~, ~15~, ~16~, 17, ~18~, 19, ~20~, ~21~, 23, ~24~, 25, ~26~, ~27~, ~28~, 29, ~30~
```

---

### 4️⃣ Next: 5

- **Cross out multiples of 5:**
  - 10, 15, 20, 25, 30

```
2, 3, ~4~, 5, ~6~, 7, ~8~, ~9~, ~10~, 11, ~12~, 13, ~14~, ~15~, ~16~, 17, ~18~, 19, ~20~, ~21~, 23, ~24~, ~25~, ~26~, ~27~, ~28~, 29, ~30~
```

---

### 5️⃣ Next: 7

- **Multiples of 7 (next uncrossed) are 14, 21, 28** (already crossed), and after that, all next are above 30.  
  - **Stop!**

---

## 🏆 Final Step: Gather All Uncrossed Numbers

**Primes ≤ 30:**
```
2, 3, 5, 7, 11, 13, 17, 19, 23, 29
```

---

## 🎨 Visual Summary

| Step | Action                      | Uncrossed (Prime) Numbers         |
|------|-----------------------------|-----------------------------------|
| 1    | Start with 2–30             | 2, 3, 4, ..., 30                  |
| 2    | Cross multiples of 2        | 2, 3, 5, 7, 9, 11, ..., 29        |
| 3    | Cross multiples of 3        | 2, 3, 5, 7, 11, 13, ..., 29       |
| 4    | Cross multiples of 5        | 2, 3, 5, 7, 11, 13, ..., 29       |
| 5    | Cross multiples of 7 (skip) | 2, 3, 5, 7, 11, 13, ..., 29       |

---

## 💡 Tips for Using the Sieve

- Only need to mark multiples up to **√N** (square root of N).
- Efficient for large N (up to millions!).
- Try implementing in your favorite programming language.

---

## 🏁 The Sieve in a Nutshell

**Write, Mark, Collect → Primes!**

---
