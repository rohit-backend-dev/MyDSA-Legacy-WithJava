```
class Solution {
    public ArrayList<ArrayList<Integer>> countFreq(int[] arr) {
       
        
        Map<Integer , Integer> map=new LinkedHashMap<>();
       
       for(int num :arr){
           map.put(num,map.getOrDefault(num,0)+1);
       }
        
        ArrayList<ArrayList<Integer>> result = new ArrayList<>();
        for (int key : map.keySet()) {
            ArrayList<Integer> pair = new ArrayList<>();
            pair.add(key);
            pair.add(map.get(key));
            result.add(pair);
        }

        return result;
    }
}
```
