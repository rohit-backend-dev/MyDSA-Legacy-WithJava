# 🍇 904. Fruit Into Baskets (Leetcode)

## 🧾 Problem Statement

You are visiting a farm that has a **single row of fruit trees** represented by an array `fruits[]`. Each tree produces a specific type of fruit, denoted by an integer (e.g., `[1, 2, 3]`).

You have **2 baskets**:

* Each basket can only hold **1 type of fruit**.
* Each basket can hold **any number** of that type.

**Rules:**

* Start at **any tree**.
* Move only **to the right**.
* Pick exactly one fruit from every tree.
* You must stop when a fruit type doesn't fit in either basket.

**Goal:**
Return the **maximum number of fruits** you can pick under these rules.

---

## 🌍 Real-World Analogy

Imagine you’re in an orchard with trees in a line. You have two baskets.

* You can collect fruit from **any tree** and move **only forward**.
* You can **only carry 2 fruit types**.
* Once you reach a tree with a **third type**, you must **stop**.

---

## 🧠 Example

### Input:

`fruits = [1, 2, 1, 2, 3]`

### Output:

`4`

### Explanation:

From index 0 → 3 → `[1, 2, 1, 2]` → 2 types → ✅
From index 1 → 4 → `[2, 1, 2, 3]` → 3 types → ❌
So max = 4 fruits.

---

## 💣 Brute Force Approach (Using HashMap)

### 🔍 Idea:

* Try starting from each tree.
* Use a HashMap to keep count of each fruit type.
* If the map has **more than 2 keys**, stop.
* Track the max window length.

### ⏱ Time Complexity:

* **O(n²)** — worst case, try every starting index.

### 💻 Java Code:

```java
class Solution {
    public int totalFruit(int[] fruits) {
        int maxFruits = 0;

        for (int i = 0; i < fruits.length; i++) {
            Map<Integer, Integer> basket = new HashMap<>();
            int count = 0;

            for (int j = i; j < fruits.length; j++) {
                basket.put(fruits[j], basket.getOrDefault(fruits[j], 0) + 1);
                if (basket.size() > 2) break;
                count++;
            }

            maxFruits = Math.max(maxFruits, count);
        }

        return maxFruits;
    }
}
```

---

## ✅ Optimal Approach — Sliding Window (Two Pointers)

### 🔍 Idea:

* Use a **window** with two pointers (`start` and `end`) to maintain a valid subarray with **at most 2 fruit types**.
* Expand the `end` pointer until invalid.
* Shrink from `start` to restore validity.
* Keep track of max window size.

---

## 📊 Tree → Basket Visualization

Let’s say:

```
fruits = [1, 2, 3, 2, 2]
```

| Index | Fruit | Baskets          | Window        | Action    |
| ----- | ----- | ---------------- | ------------- | --------- |
| 0     | 1     | {1}              | \[1]          | Expand    |
| 1     | 2     | {1, 2}           | \[1, 2]       | Expand    |
| 2     | 3     | {1, 2, 3} ❌      |               | Shrink    |
|       |       | remove 1 → {2,3} | \[2,3]        | Restore   |
| 3     | 2     | {2, 3}           | \[2, 3, 2]    | Expand    |
| 4     | 2     | {2, 3}           | \[2, 3, 2, 2] | ✅ max = 4 |

---

### 💻 Java Code:

```java
class Solution {
    public int totalFruit(int[] fruits) {
        Map<Integer, Integer> basket = new HashMap<>();
        int left = 0, maxFruits = 0;

        for (int right = 0; right < fruits.length; right++) {
            basket.put(fruits[right], basket.getOrDefault(fruits[right], 0) + 1);

            while (basket.size() > 2) {
                basket.put(fruits[left], basket.get(fruits[left]) - 1);
                if (basket.get(fruits[left]) == 0) {
                    basket.remove(fruits[left]);
                }
                left++;
            }

            maxFruits = Math.max(maxFruits, right - left + 1);
        }

        return maxFruits;
    }
}
```

---
## 📘 Summary Table

| Approach       | Time Complexity | Space Complexity | Description               |
| -------------- | --------------- | ---------------- | ------------------------- |
| Brute Force    | O(n²)           | O(1)             | Try every starting index  |
| Sliding Window | O(n)            | O(1)             | Expand/shrink dynamically |


---
# Note   

### 🔹 **What is `getOrDefault()`?**

Imagine a basket where you store fruit types and how many you have.

If someone asks:

> "How many bananas do you have?"

But you **never added bananas**, then `getOrDefault("banana", 0)` simply says:

> "I don’t know about bananas, so just take 0."

---

### 🔹 **Simple Code Example 

```java
Map<String, Integer> map = new HashMap<>();
map.put("apple", 3);

int count = map.getOrDefault("apple", 0);  // returns 3
int count2 = map.getOrDefault("banana", 0); // returns 0, because "banana" is not in the map
```

### 🔹 Without `getOrDefault()` (Old way):

```java
if (basket.containsKey(1)) {
    basket.put(1, basket.get(1) + 1);
} else {
    basket.put(1, 1);
}
```

