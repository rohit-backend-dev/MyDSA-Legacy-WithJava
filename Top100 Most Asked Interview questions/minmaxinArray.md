
https://www.geeksforgeeks.org/problems/find-minimum-and-maximum-element-in-an-array4428/1

```
class Solution {
    public Pair<Integer, Integer> getMinMax(int[] arr) {

        
        int n=arr.length;
        
        int min = arr[0];
        int max=arr[0];
        
       for (int i = 1; i < n; i++) {
            if (arr[i] < min) min = arr[i];
            if (arr[i] > max) max = arr[i];
        }

        return new Pair<>(min, max);
    }
}
```
