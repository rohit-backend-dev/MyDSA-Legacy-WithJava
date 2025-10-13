# Brute force
```
import java.util.Arrays;

class Solution {
    public int threeSumClosest(int[] nums, int target) {
        Arrays.sort(nums);  // optional, not required for triple loop
        int n = nums.length;
        int closestSum = nums[0] + nums[1] + nums[2]; // initialize with first three elements

        for (int i = 0; i < n - 2; i++) {
            for (int j = i + 1; j < n - 1; j++) {
                for (int k = j + 1; k < n; k++) {
                    int sum = nums[i] + nums[j] + nums[k];
                    if (Math.abs(sum - target) < Math.abs(closestSum - target)) {
                        closestSum = sum; // update if this sum is closer to target
                    }
                }
            }
        }

        return closestSum;
    }
}


```

# Optimal using two pointer


```
import java.util.Arrays;
class Solution {
   public int threeSumClosest(int[] nums, int target) {
       
       Arrays.sort(nums);
       int n = nums.length;
       int closestSum = nums[0] + nums[1] + nums[2];

       for (int k = 0; k <= n - 3; k++) {
           int i = k + 1;
           int j = n - 1;

           while (i < j) {
               int sum = nums[k] + nums[i] + nums[j];

               // update closestSum if current sum is closer
               if (Math.abs(target - sum) < Math.abs(target - closestSum)) {
                   closestSum = sum;
               }

               // pointer movement (outside the if block)
               if (sum < target) {
                   i++;
               } else if (sum > target) {
                   j--;
               } else {
                   // exact match found
                   return sum;
               }
           }
       }

       return closestSum;
    }
}


```
