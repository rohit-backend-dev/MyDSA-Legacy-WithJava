
## **1. Brute Force Approach**

* **Logic:** Check every possible pair.
* **Time Complexity:** O(n²)
* **Space Complexity:** O(1)

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) { // avoid duplicates
                if (nums[i] + nums[j] == target) {
                    return new int[]{i, j};
                }
            }
        }
        return new int[]{}; // No solution found
    }
}
```


## **2. Optimal Approach (HashMap)**

* **Logic:** Store each number’s index in a map, and check if the complement exists.
* **Time Complexity:** O(n)
* **Space Complexity:** O(n)

```java
import java.util.HashMap;

class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>(); // value → index

        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];

            if (map.containsKey(complement)) {
                return new int[]{map.get(complement), i}; // found the pair
            }

            map.put(nums[i], i); // store current value and index
        }

        return new int[]{}; // No solution found
    }
}
```
