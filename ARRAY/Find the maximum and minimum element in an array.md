```
class Solution {
    public Pair<Integer, Integer> getMinMax(int[] arr) {
        // Code Here
        int min=Integer.MAX_VALUE;
        int max=Integer.MIN_VALUE;
        int n= arr.length;
        
        for(int i=0;i<n;i++){
            if(arr[i] < min ) {
              min= arr[i];
            }
            if(arr[i] > max){
                max=arr[i];
            }
        }
        return new Pair<>(min, max);
    }
}
```

    *Time Complexity: O(n) - Single pass through the array.*
    *Space Complexity: O(1) - Only two extra variables are used.*
