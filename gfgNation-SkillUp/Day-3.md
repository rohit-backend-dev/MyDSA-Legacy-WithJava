# 📚 Power of K in n! 

---

## 1️⃣ **What is the Problem?**

**🎯 Problem Statement**:  
Given two integers **n** and **k**, find the largest integer **e** such that **kᵉ divides n!** completely.

### ✨ In Simple Words
How many times can we multiply **k** with itself so that it perfectly divides **n!** without remainder?

---

## 2️⃣ **Why Does This Problem Exist?**

- **Factorials** grow fast and contain many prime factors.
- We want to know: **how many full sets of k can be "packed" into n!**
- **Analogy**:
- Real-Life Thought:
- Suppose you have n! chocolates.
- Each kᵉ is a special chocolate box.
- How many full boxes can you make?

---

## 3️⃣ **How Do We Approach This?**

### Case 1: **k is Prime**
- Use **Legendre’s Formula** to count its power in n!

### Case 2: **k is Composite**
- Split k into its **prime factors**.
- For each prime, count its power in n! and divide by its exponent in k.
- The **minimum among them** is the answer.

---

## 4️⃣ **Legendre’s Formula (Why & How)**

### Why?
Counts **how many times a prime p divides n!**, including all its multiples (p, p², p³, ...).

### How?
> **Power of p in n! = floor(n/p) + floor(n/p²) + floor(n/p³) + ...** until term becomes 0

#### Example:
For n = 10, p = 2:  
- floor(10/2) = 5  
- floor(10/4) = 2  
- floor(10/8) = 1  
- floor(10/16) = 0 (stop)  
**Total = 5 + 2 + 1 = 8**  
So, 2⁸ divides 10!

---

## 5️⃣ **Composite k — The Twist!**

### Why?
k is made of multiple primes, so each must have enough presence in n! for kᵉ to divide n!.

### How?
1. Factorize k into primes: `k = p₁^q₁ × p₂^q₂ × ...`
2. For each prime pᵢ:
   - Count power in n! using Legendre’s formula.
   - Divide by its exponent in k: `power_pᵢ_in_n! ÷ qᵢ`
3. **Answer = Minimum of all these values**

---

## 6️⃣ **Examples**

### ✅ Example 1: n = 10, k = 2

**Step 1:** Is k a prime?  
✔️ Yes, k = 2 (prime).

**Step 2:** How many times does 2 divide 10!?

**Apply Legendre’s Formula:**

- 10 ÷ 2 = 5  
- 10 ÷ 4 = 2  
- 10 ÷ 8 = 1  
- Next term → 10 ÷ 16 = 0 → STOP  
- **Total Power of 2 in 10! = 5 + 2 + 1 = 8**

✅ **Answer = 8**

---

### ✅ Example 2: n = 100, k = 5

**Step 1:** Is k a prime?  
✔️ Yes, k = 5 (prime).

**Step 2:** How many times does 5 divide 100!?

**Apply Legendre’s Formula:**

- 100 ÷ 5 = 20  
- 100 ÷ 25 = 4  
- 100 ÷ 125 = 0 → STOP  
- **Total Power of 5 = 20 + 4 = 24**

✅ **Answer = 24**

---

### ✅ Example 3: n = 10, k = 6

**Step 1:** Is k a prime?  
❌ No, k = 6 (composite).

**Step 2:** Factorize k → 6 = 2¹ × 3¹

**Step 3:** Power of 2 in 10!:

- 10 ÷ 2 = 5  
- 10 ÷ 4 = 2  
- 10 ÷ 8 = 1  
- **Total = 5 + 2 + 1 = 8**
- Adjust by exponent in k = 1  
- 👉 8 ÷ 1 = 8

**Step 4:** Power of 3 in 10!:

- 10 ÷ 3 = 3  
- 10 ÷ 9 = 1  
- **Total = 3 + 1 = 4**
- Adjust by exponent in k = 1  
- 👉 4 ÷ 1 = 4

**Step 5:** Minimum = min(8, 4) = 4

✅ **Answer = 4**

---

## 8️⃣ **Java Code — Explained Step By Step**

```java
public class PowerOfKInN {
    // Returns the highest power e such that k^e divides n!
    public static int highestPower(int n, int k) {
        int result = Integer.MAX_VALUE;  // Start big; we're looking for the minimum
        int num = k;  // We'll factorize k

        // 1. Factorize k into primes up to sqrt(k)
        for (int i = 2; i * i <= num; i++) {
            if (num % i == 0) { // Found a prime factor
                int count = 0;
                while (num % i == 0) { // Count its exponent in k
                    count++;
                    num /= i;
                }
                // 2. Use Legendre's formula for power of i in n!
                int temp = 0, p = i;
                while (p <= n) {
                    temp += n / p;
                    p *= i;
                }
                // 3. Divide by its exponent in k, update result
                result = Math.min(result, temp / count);
            }
        }

        // 4. If there's a remaining prime factor > sqrt(k)
        if (num > 1) {
            int temp = 0, p = num;
            while (p <= n) {
                temp += n / p;
                p *= num;
            }
            result = Math.min(result, temp); // Its exponent in k is 1
        }

        return result; // This is the answer: largest e so k^e divides n!
    }

    public static void main(String[] args) {
        System.out.println(highestPower(10, 6)); // Output: 4
    }
}
```

**Line-by-Line Story:**
- **result = Integer.MAX_VALUE**: We want the minimum among all prime factors.
- **num = k**: We'll break k apart.
- **for (int i = 2; ...)**: Try all possible primes up to sqrt(k).
- **if (num % i == 0)**: Found a prime that divides k.
- **while (num % i == 0)**: Count how many times (exponent) it divides k.
- **Legendre's formula loop**: Counts power of prime in n!.
- **result = Math.min(result, temp / count)**: Adjust by exponent and keep the lowest.
- **If num > 1**: After loop, if anything’s left it’s a large prime; treat similarly.
- **return result**: That’s our answer.

---

## 9️⃣ **Quick Dry-Run Table**

| n   | k | Answer | Reason              |
|-----|---|--------|---------------------|
| 10  | 2 | 8      | 2⁸ divides 10!      |
| 100 | 5 | 24     | 5²⁴ divides 100!    |
| 10  | 6 | 4      | min(2⁸/1, 3⁴/1) = 4 |

---
