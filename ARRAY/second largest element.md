```
class Solution {
    public int getSecondLargest(int[] arr) {
        // code here
        int firstLargest=Integer.MIN_VALUE;
        int secondLargest=Integer.MIN_VALUE;
        
        for(int num : arr){
            if(num>firstLargest){
                secondLargest=firstLargest;
               firstLargest =num;
            }
            else if (num>secondLargest && num != firstLargest){
                secondLargest=num;
            }
        }
        return secondLargest;
    }
}
```



# OR


```
class Solution {
    public int getSecondLargest(int[] arr) {
        int firstLargest = Integer.MIN_VALUE;
        int secondLargest = Integer.MIN_VALUE;

        for (int num : arr) {
            if (num > firstLargest) {
                secondLargest = firstLargest; // shift old max
                firstLargest = num;           // new max
            } else if (num > secondLargest && num != firstLargest) {
                secondLargest = num;
            }
        }

        // If no second largest exists (like all elements same)
        return (secondLargest == Integer.MIN_VALUE) ? -1 : secondLargest;
    }
}

```
