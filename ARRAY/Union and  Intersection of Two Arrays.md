# **1. Intersection of Two Arrays**

```java
import java.util.*;

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

* **Time Complexity:** O(n + m)

  * n = length of nums1, m = length of nums2
* **Space Complexity:** O(n + m)

  * Storing elements in two sets

---

# **2. Union of Two Arrays**

```java
import java.util.*;

class Solution {
    public static ArrayList<Integer> findUnion(int a[], int b[]) {
        Set<Integer> set = new HashSet<>();
        
        // Add all elements from array a
        for (int num : a) set.add(num);
        
        // Add all elements from array b
        for (int num : b) set.add(num);
        
        // Convert set to ArrayList
        ArrayList<Integer> unionList = new ArrayList<>(set);
        
        // Optional: sort the union list
        Collections.sort(unionList);
        
        return unionList;
    }
}
```

* **Time Complexity:**

  * Adding elements to HashSet: O(n + m)
  * Converting to ArrayList: O(k) where k ≤ n + m
  * Sorting (optional): O(k log k)

* **Space Complexity:** O(n + m) → storing all unique elements in the set

