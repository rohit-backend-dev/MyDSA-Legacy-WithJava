## **1. Nested Loop Solution**

```java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        Set<Integer> resultSet = new HashSet<>();
        
        // Nested loop to check every pair
        for (int i = 0; i < nums1.length; i++) {
            for (int j = 0; j < nums2.length; j++) {
                if (nums1[i] == nums2[j]) { // compare values, not indices
                    resultSet.add(nums1[i]); // add to result set to avoid duplicates
                    break; // no need to check further for this nums1[i]
                }
            }
        }
        
        // Convert set to array
        int[] result = new int[resultSet.size()];
        int k = 0;
        for (int num : resultSet) {
            result[k++] = num;
        }
        return result;
    }
}
```

**Time Complexity:** O(n × m)
**Space Complexity:** O(min(n, m)) for the result set
---

## **2. HashSet Optimized Solution**

```java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        Set<Integer> set1 = new HashSet<>();
        for (int num : nums1) set1.add(num);

        Set<Integer> resultSet = new HashSet<>();
        for (int num : nums2) {
            if (set1.contains(num)) resultSet.add(num);
        }

        int[] result = new int[resultSet.size()];
        int i = 0;
        for (int num : resultSet) result[i++] = num;
        return result;
    }
}
```

**Time Complexity:** O(n + m)
**Space Complexity:** O(n + m) for two sets

