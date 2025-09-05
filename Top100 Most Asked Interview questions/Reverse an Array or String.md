```https://www.geeksforgeeks.org/dsa/program-to-reverse-an-array/```

```
class Solution {
    public static String reverseString(String s) {
        // code here
      
      char[] arr= s.toCharArray();
      int i=0,j=arr.length-1;
      
      while(i<j){
          char temp = arr[i];
          arr[i]=arr[j];
          arr[j]=temp;
          
          i++;
          j--;
      }
      return new String(arr);
    }
}
```
