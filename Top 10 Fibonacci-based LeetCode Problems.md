# **Top 10 Fibonacci-based LeetCode Problems – Java Solutions**

---

## **1. Fibonacci Number** (LeetCode 509)

**Recurrence:** `F(n) = F(n-1) + F(n-2)`

```java
class Solution {
    public static int fibonacciNumber(int n) {
        if (n == 0) return 0;
        if (n == 1) return 1;

        int a = 0, b = 1, c = 0;
        for (int i = 2; i <= n; i++) {
            c = a + b;
            a = b;
            b = c;
        }
        return b;
    }
}
```

**Example:** `n=5` → Output: `5`

---

## **2. Climbing Stairs** (LeetCode 70)

**Recurrence:** `ways(n) = ways(n-1) + ways(n-2)`

```java
class Solution {
    public int climbStairs(int n) {
        if (n <= 2) return n;

        int a = 1, b = 2, c = 0;
        for (int i = 3; i <= n; i++) {
            c = a + b;
            a = b;
            b = c;
        }
        return b;
    }
}
```

**Example:** `n=5` → Output: `8`

---

## **3. Min Cost Climbing Stairs** (LeetCode 746)

**Recurrence:** `dp[i] = cost[i] + min(dp[i-1], dp[i-2])`

```java
class Solution {
    public int minCostClimbingStairs(int[] cost) {
        int n = cost.length;
        int a = cost[0], b = cost[1], c = 0;

        for (int i = 2; i < n; i++) {
            c = cost[i] + Math.min(a, b);
            a = b;
            b = c;
        }
        return Math.min(a, b);
    }
}
```

**Example:** `cost=[10,15,20]` → Output: `15`

---

## **4. Tribonacci Number** (LeetCode 1137)

**Recurrence:** `T(n) = T(n-1) + T(n-2) + T(n-3)`

```java
class Solution {
    public int tribonacci(int n) {
        if (n == 0) return 0;
        if (n == 1 || n == 2) return 1;

        int a = 0, b = 1, c = 1, d = 0;
        for (int i = 3; i <= n; i++) {
            d = a + b + c;
            a = b;
            b = c;
            c = d;
        }
        return c;
    }
}
```

**Example:** `n=4` → Output: `4`

---

## **5. House Robber** (LeetCode 198)

**Recurrence:** `dp[i] = max(dp[i-1], dp[i-2] + nums[i])`

```java
class Solution {
    public int rob(int[] nums) {
        int n = nums.length;
        if (n == 1) return nums[0];

        int a = nums[0], b = Math.max(nums[0], nums[1]), c = 0;
        for (int i = 2; i < n; i++) {
            c = Math.max(b, a + nums[i]);
            a = b;
            b = c;
        }
        return b;
    }
}
```

**Example:** `nums=[1,2,3,1]` → Output: `4`

---

## **6. House Robber II** (LeetCode 213)

**Circular houses:** max of `rob(0…n-2)` or `rob(1…n-1)`

```java
class Solution {
    public int rob(int[] nums) {
        if (nums.length == 1) return nums[0];
        return Math.max(robLinear(nums, 0, nums.length - 2), robLinear(nums, 1, nums.length - 1));
    }

    private int robLinear(int[] nums, int start, int end) {
        int a = 0, b = 0, c;
        for (int i = start; i <= end; i++) {
            c = Math.max(b, a + nums[i]);
            a = b;
            b = c;
        }
        return b;
    }
}
```

---

## **7. Decode Ways** (LeetCode 91)

**Recurrence:** `dp[i] = dp[i-1] + dp[i-2]` if valid

```java
class Solution {
    public int numDecodings(String s) {
        if (s.charAt(0) == '0') return 0;
        int a = 1, b = 1, c = 0;

        for (int i = 1; i < s.length(); i++) {
            c = 0;
            if (s.charAt(i) != '0') c += b;
            int twoDigit = Integer.parseInt(s.substring(i-1, i+1));
            if (twoDigit >= 10 && twoDigit <= 26) c += a;
            a = b;
            b = c;
        }
        return b;
    }
}
```

---

## **8. Fibonacci Number with large n (optimized)**

**Fast doubling / iterative version:** Already covered in #1. Use `long` if `n` is large.

```java
// Same as #1 but with long to avoid overflow
class Solution {
    public static long fibonacciNumber(int n) {
        if (n == 0) return 0L;
        if (n == 1) return 1L;

        long a = 0L, b = 1L, c = 0L;
        for (int i = 2; i <= n; i++) {
            c = a + b;
            a = b;
            b = c;
        }
        return b;
    }
}
```

---

## **9. Number of Ways to Reach N-th Stair (1,2,3 steps)**

**Recurrence:** `ways(n) = ways(n-1) + ways(n-2) + ways(n-3)`

```java
class Solution {
    public int countWays(int n) {
        if (n == 0) return 1;
        if (n == 1) return 1;
        if (n == 2) return 2;

        int a = 1, b = 1, c = 2, d = 0;
        for (int i = 3; i <= n; i++) {
            d = a + b + c;
            a = b;
            b = c;
            c = d;
        }
        return c;
    }
}
```

---

## **10. Paint Fence Problem** (LeetCode 276)

**Recurrence:** `dp[i] = (k-1)*(dp[i-1]+dp[i-2])` → Fibonacci-like

```java
class Solution {
    public int numWays(int n, int k) {
        if (n == 0) return 0;
        if (n == 1) return k;

        int a = k; // 1 fence
        int b = k * k; // 2 fences
        int c = 0;

        for (int i = 3; i <= n; i++) {
            c = (k - 1) * (a + b);
            a = b;
            b = c;
        }
        return b;
    }
}
```

