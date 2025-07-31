### 🔶 **Problem Statement**

You're given an array of **intervals**. Each interval is a closed range \[start, end].
You're also given an integer `k`.
An integer is **Powerful** if it appears in **at least `k` intervals**.

👉 You need to **find the maximum such Powerful integer**. If no such integer exists, return `-1`.

---

### 🔍 **Example**

```java
Input: intervals = [[1,3], [4,6], [3,4]], k = 2
```

* Interval 1: 1, 2, 3
* Interval 2: 4, 5, 6
* Interval 3: 3, 4

🔹 Count of each number:

* 1 → 1
* 2 → 1
* 3 → 2 ✅
* 4 → 2 ✅
* 5 → 1
* 6 → 1

✅ Powerful Integers (appear in ≥2 intervals): **3, 4**

🎯 **Maximum Powerful Integer**: `4`

---

## 🔁 Brute-Force Approach (with Explanation)

### ✅ Intuition:

We count how many times each number appears in different intervals.

### 🧠 Steps:

1. Create a frequency map or array to store how many intervals each number is part of.
2. Traverse each interval and update the count for each integer in the range.
3. After processing all intervals, check which numbers have frequency ≥ k.
4. Return the **maximum** such number.

### ⏱ Time Complexity:

* Worst case: O(N \* Range)
  (Range being the difference between start and end of intervals)

---

### 💻 Brute-Force Java Code

```java
import java.util.*;

public class PowerfulIntegerBruteForce {
    public static int findMaxPowerfulInteger(int[][] intervals, int k) {
        Map<Integer, Integer> freq = new HashMap<>();

        for (int[] interval : intervals) {
            for (int i = interval[0]; i <= interval[1]; i++) {
                freq.put(i, freq.getOrDefault(i, 0) + 1);
            }
        }

        int max = -1;
        for (Map.Entry<Integer, Integer> entry : freq.entrySet()) {
            if (entry.getValue() >= k) {
                max = Math.max(max, entry.getKey());
            }
        }

        return max;
    }

    public static void main(String[] args) {
        int[][] intervals = {{1,3}, {4,6}, {3,4}};
        int k = 2;
        System.out.println(findMaxPowerfulInteger(intervals, k)); // Output: 4
    }
}
```

---

### ✅Intuition

We need to:

* Track the ranges where `count >= k`
* For each such range, update the `maxPowerful` as the **end of the range**

This ensures we consider all powerful integers, **not just the boundaries**.

---

### 🔢 Formula:
Let map[i] be the net change at position i.

At start: map[start] += 1

At end + 1: map[end + 1] -= 1


### ⏱ Time Complexity:
O(N log N), due to TreeMap sorting

---

### ✅ Optimal Java Code

```java
import java.util.*;

public class PowerfulIntegerFixed {
    public static int findMaxPowerfulInteger(int[][] intervals, int k) {
        TreeMap<Integer, Integer> map = new TreeMap<>();

        for (int[] interval : intervals) {
            map.put(interval[0], map.getOrDefault(interval[0], 0) + 1);
            map.put(interval[1] + 1, map.getOrDefault(interval[1] + 1, 0) - 1);
        }

        int count = 0;
        int prev = -1;
        int maxPowerful = -1;

        for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
            int point = entry.getKey();

            if (count >= k && prev != -1) {
                // Current segment [prev, point - 1] is powerful
                maxPowerful = Math.max(maxPowerful, point - 1);
            }

            count += entry.getValue();
            prev = point;
        }

        return maxPowerful;
    }

    public static void main(String[] args) {
        int[][] intervals = {
            {1, 10},
            {5, 21},
            {18, 30}
        };
        int k = 2;
        System.out.println(findMaxPowerfulInteger(intervals, k)); // ✅ Output: 21
    }
}
```

---

### ✅ How it Works

Let’s say you have:

```java
intervals = { [1, 10], [5, 21], [18, 30] }
k = 2
```

🧮 Overlaps:

* 5 to 10 → in 2 intervals
* 18 to 21 → in 2 or more intervals

---


## 📌 Summary

| Approach    | Time       | Space | Idea                                  |
| ----------- | ---------- | ----- | ------------------------------------- |
| Brute Force | O(N \* R)  | O(R)  | Count each number in each interval    |
| Optimal     | O(N log N) | O(N)  | Use sweep line / prefix sum technique |
