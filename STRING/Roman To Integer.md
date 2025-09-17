```
class Solution {
    public int romanToInt(String s) {
        // Roman numeral map
        Map<Character, Integer> map = new HashMap<>();
        map.put('I', 1);
        map.put('V', 5);
        map.put('X', 10);
        map.put('L', 50);
        map.put('C', 100);
        map.put('D', 500);
        map.put('M', 1000);

        int n = s.length();
        int result = 0;

        for (int i = 0; i < n; i++) {
            int value = map.get(s.charAt(i));

            // if next char exists and is greater → subtract
            if (i < n - 1 && value < map.get(s.charAt(i + 1))) {
                result -= value;
            } else {
                result += value;
            }
        }
        return result;
    }
}

```
