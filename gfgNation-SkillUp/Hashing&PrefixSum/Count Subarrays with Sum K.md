To solve the **"Count Subarrays with Sum K"** problem, we want to find how many subarrays in a given array have a sum exactly equal to `K`.

---

## 🔸 Problem Statement

Given an array of integers `nums` and an integer `k`, return the total number of **continuous subarrays** whose sum equals to `k`.

---

Let’s explore **all three approaches**:

---

## 🧠 1. Brute Force (O(n³))

### ✅ Idea:

Try all possible subarrays and compute the sum of each. Count the ones that match `k`.

### 🔢 Code:

```java
public int subarraySumBrute(int[] nums, int k) {
    int n = nums.length;
    int count = 0;
    
    for (int i = 0; i < n; i++) {
        for (int j = i; j < n; j++) {
            int sum = 0;
            for (int p = i; p <= j; p++) {
                sum += nums[p];
            }
            if (sum == k) count++;
        }
    }
    return count;
}
```

### ⏱️ Time Complexity:

* **O(n³)** — 3 nested loops

---

## 🧠 2. Better Approach (O(n²))

### ✅ Idea:

Avoid recomputing the sum every time by maintaining a running sum.

### 🔢 Code:

```java
public int subarraySumBetter(int[] nums, int k) {
    int n = nums.length;
    int count = 0;
    
    for (int i = 0; i < n; i++) {
        int sum = 0;
        for (int j = i; j < n; j++) {
            sum += nums[j];
            if (sum == k) count++;
        }
    }
    return count;
}
```

### ⏱️ Time Complexity:

* **O(n²)** — two nested loops
* **O(1)** space

---

## 🧠 3. Optimal Approach using HashMap (Prefix Sum + Hashing) — O(n)

### ✅ Idea:

Use a HashMap to store **prefix sums** and their frequencies.

### 📌 Observation:

If the current prefix sum is `sum`, and there's a previous prefix sum `sum - k`, then the subarray between them adds up to `k`.

### 🔢 Code:

```java
public int subarraySumOptimal(int[] nums, int k) {
    Map<Integer, Integer> prefixSumFreq = new HashMap<>();
    prefixSumFreq.put(0, 1); // base case

    int sum = 0, count = 0;
    
    for (int num : nums) {
        sum += num;
        
        if (prefixSumFreq.containsKey(sum - k)) {
            count += prefixSumFreq.get(sum - k);
        }
        
        prefixSumFreq.put(sum, prefixSumFreq.getOrDefault(sum, 0) + 1);
    }

    return count;
}
```

### 🧠 Dry Run:

For `nums = [1, 2, 3], k = 3`

* Prefix sums: 1, 3 → we find subarrays like \[1,2] and \[3]

### ⏱️ Time Complexity:

* **O(n)** — one pass
* **O(n)** space for hashmap

---

## 🔚 Summary Table

| Approach    | Time Complexity | Space | Notes                              |
| ----------- | --------------- | ----- | ---------------------------------- |
| Brute Force | O(n³)           | O(1)  | Slow, not usable for large arrays  |
| Better      | O(n²)           | O(1)  | Still inefficient for large inputs |
| Optimal     | O(n)            | O(n)  | Best for real use cases            |
