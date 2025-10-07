
### **Solution 1 – Using a HashSet and Single Counter**

```java
import java.util.*;

class Solution {
    public boolean halvesAreAlike(String s) {
        Set<Character> vowels = new HashSet<>(Arrays.asList('a','e','i','o','u','A','E','I','O','U'));
        int n = s.length(), mid = n / 2;
        int count = 0;

        for (int i = 0; i < mid; i++) {
            if (vowels.contains(s.charAt(i))) count++;
        }
        for (int i = mid; i < n; i++) {
            if (vowels.contains(s.charAt(i))) count--;
        }

        return count == 0;
    }
}
```


### **Solution 2 – Using Two Counters and a Helper Method**

```java
class Solution {
    public boolean halvesAreAlike(String s) {
        int n = s.length();
        int half = n / 2;
        int count1 = 0, count2 = 0;

        for (int i = 0; i < half; i++) {
            if (isVowel(s.charAt(i))) count1++;
        }

        for (int i = half; i < n; i++) {
            if (isVowel(s.charAt(i))) count2++;
        }

        return count1 == count2;
    }

    private boolean isVowel(char c) {
        c = Character.toLowerCase(c);
        return (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u');
    }
}
```

]
