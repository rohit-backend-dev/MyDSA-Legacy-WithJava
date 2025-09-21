 **“Best Time to Buy and Sell Stock I”**

---

# **Solution 1: Min-Price Tracking**

```java
class Solution {
    public int maxProfit(int[] prices) {
        int minPrice = Integer.MAX_VALUE; // track lowest price so far
        int maxProfit = 0;                // max profit

        for (int i = 0; i < prices.length; i++) {
            // Update minimum price so far
            if (prices[i] < minPrice) {
                minPrice = prices[i];
            }

            // Calculate profit if we sell today
            int profit = prices[i] - minPrice;

            // Update maximum profit
            if (profit > maxProfit) {
                maxProfit = profit;
            }
        }

        return maxProfit;
    }
}
```

### ✅ How It Works

1. Keep track of the **lowest price** (`minPrice`) seen so far.
2. For each day, calculate potential profit if sold today: `profit = prices[i] - minPrice`.
3. Update the **maximum profit** found so far.

**Key Insight:**

* You never sell before buying because `minPrice` always comes from previous days.

---

### 🔹 Complexity

* **Time:** O(n) → Single pass through the array
* **Space:** O(1) → Only two extra variables

---

# **Solution 2: BuyDay Tracking (Similar Idea)**

```java
class Solution {
    public int maxProfit(int[] prices) {
        int buyDay = prices[0]; // lowest price seen so far
        int profit = 0;         // max profit

        for (int i = 1; i < prices.length; i++) {
            // potential profit if we sell today
            int cost = prices[i] - buyDay;
            profit = Math.max(profit, cost);

            // update buyDay if we find a lower price
            if (prices[i] < buyDay) {
                buyDay = prices[i];
            }
        }

        return profit;
    }
}
```

### ✅ How It Works

* `buyDay` = minimum price seen so far (same as `minPrice`).
* `cost` = profit if selling today.
* Update `profit` with `Math.max(profit, cost)`.
* Update `buyDay` if a new lower price is found.

**Observation:**

* Both solutions are logically identical. The difference is just in **variable naming**.

---

### 🔹 Complexity

* **Time:** O(n) → single pass
* **Space:** O(1) → only `buyDay` and `profit`

---

