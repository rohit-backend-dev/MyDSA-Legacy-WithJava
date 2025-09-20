## **1️⃣ Sliding Window with Window Sum **

```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int left = 0;
        int ans = 0;        // Store max consecutive 1s
        int window = 0;     // Current window sum

        for (int right = 0; right < nums.length; right++) {
            window += nums[right];   // Add current element to window

            // Shrink the window if it contains any 0
            while (right - left + 1 != window) {
                window -= nums[left]; // Remove left element from window
                left++;
            }

            ans = Math.max(ans, right - left + 1); // Update max length
        }

        return ans;
    }
}
```

**Explanation:**

* `window` counts the number of `1`s in the current window.
* `right - left + 1` is the **window size**.
* If the window has a `0`, then `window < right - left + 1`, so we shrink it from the left.
* `ans` is updated with the maximum window length of consecutive `1`s.

**Time Complexity:** `O(n)`
**Space Complexity:** `O(1)`

✅ Works well when you want a **sliding window approach**.

---

## **2️⃣ Simple Run-Length Count (Most Common)**

```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int maxCount = 0;
        int count = 0;

        for (int num : nums) {
            if (num == 1) {
                count++;  // Increment current streak of 1s
                maxCount = Math.max(maxCount, count);
            } else {
                count = 0;  // Reset streak if 0 encountered
            }
        }

        return maxCount;
    }
}
```

**Explanation:**

* Keep a **running count** of consecutive `1`s.
* Reset the count to `0` whenever a `0` appears.
* Update `maxCount` on each iteration.

**Time Complexity:** `O(n)`
**Space Complexity:** `O(1)`

✅ This is the **simplest and most efficient approach**, preferred in interviews.

