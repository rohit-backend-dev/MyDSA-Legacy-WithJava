## **1️⃣ Brute Force**

**Logic:**
Check every possible pair `(buyDay, sellDay)` where `sellDay > buyDay` and calculate profit. Keep the max.

**Time Complexity:** `O(n²)` (nested loops)
**Space Complexity:** `O(1)` (no extra storage)

**Code:**

```java
class Solution {
    public int maxProfit(int[] prices) {
        int maxProfit = 0;
        int n = prices.length;

        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                int profit = prices[j] - prices[i];
                if (profit > maxProfit) {
                    maxProfit = profit;
                }
            }
        }

        return maxProfit;
    }
}
```

---

## **2️⃣ Better Approach**

**Logic:**
Instead of checking all pairs,

* Keep track of the **minimum price so far** while iterating.
* For each day, calculate `currentProfit = prices[i] - minPriceSoFar` and update max profit.

**Time Complexity:** `O(n)` (single loop)
**Space Complexity:** `O(1)`

**Code:**

```java
class Solution {
    public int maxProfit(int[] prices) {
        int n = prices.length;
        int maxProfit = 0;

        for (int i = 0; i < n; i++) {
            int minPrice = prices[i];
            for (int j = i + 1; j < n; j++) {
                int profit = prices[j] - minPrice;
                if (profit > maxProfit) {
                    maxProfit = profit;
                }
            }
        }

        return maxProfit;
    }
}
```

> This is **still O(n²)** in worst case, so not truly optimal — but better structured.

---

## **3️⃣ Optimal Approach (Best Time)**

**Logic:**
Track **minimum price so far** in a single pass.
At each step:

* Update min price if the current price is lower.
* Calculate profit with `currentPrice - minPrice` and update max profit if better.

**Time Complexity:** `O(n)`
**Space Complexity:** `O(1)`

**Code:**

```java
class Solution {
    public int maxProfit(int[] prices) {
        int minPrice = Integer.MAX_VALUE; // Step 1: Start with largest possible value
        int maxProfit = 0;                // Step 2: Start with zero profit

        // Step 3: Loop through each day's price
        for (int i = 0; i < prices.length; i++) {
            int price = prices[i]; // Current day's stock price

            // Step 4: If today's price is lower than any before, update minPrice
            if (price < minPrice) {
                minPrice = price; 
            }
            // Step 5: Else, check if selling today gives more profit than before
            else if (price - minPrice > maxProfit) {
                maxProfit = price - minPrice; 
            }
        }

        // Step 6: Return the maximum profit found
        return maxProfit;
    }
}

```
