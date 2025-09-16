```java
class Solution {
    public String longestCommonPrefix(String[] str) {
        
        StringBuilder result = new StringBuilder();

        Arrays.sort(str);

        char[] first=str[0].toCharArray();
        char[] last=str[str.length-1].toCharArray();

        for(int i=0;i<first.length;i++){
            if(first[i] != last[i]){
                break;
               
            }
             result.append(first[i]);
        }
        return result.toString();
    }
}
```
