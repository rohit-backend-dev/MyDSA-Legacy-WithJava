
```
int firstLargest = Integer.MIN_VALUE;

for (int num : arr) {
    if (num > firstLargest) {
        firstLargest = num;
    }
}
return firstLargest;

```

## OR

```
class Solution {
    public static int largest(int[] arr) {
        // code here
        int n=arr.length;
        int max=arr[0];
        
        for(int i=0;i<n;i++){
            if(arr[i]>max){
                max= arr[i];
            }
        }
        return max;
    }
}

```
