Here’s how you can **convert a Roman numeral to an integer** in Java:

---

### ✅ Roman Numeral Rules:

Roman numerals are based on these 7 symbols:

| Symbol | Value |
| ------ | ----- |
| I      | 1     |
| V      | 5     |
| X      | 10    |
| L      | 50    |
| C      | 100   |
| D      | 500   |
| M      | 1000  |

If a smaller value appears before a larger one, it is **subtracted**, e.g.:

* IV = 4
* IX = 9
* XL = 40

---

### 🔧 Java Code (Efficient & Clean)

```java
import java.util.*;

public class RomanToInteger {
    public static int romanToInt(String s) {
        Map<Character, Integer> romanMap = new HashMap<>();
        romanMap.put('I', 1);
        romanMap.put('V', 5);
        romanMap.put('X', 10);
        romanMap.put('L', 50);
        romanMap.put('C', 100);
        romanMap.put('D', 500);
        romanMap.put('M', 1000);

        int result = 0;
        int prev = 0;

        for (int i = s.length() - 1; i >= 0; i--) {
            int current = romanMap.get(s.charAt(i));

            if (current < prev) {
                result -= current; // Subtract if smaller value before larger
            } else {
                result += current; // Otherwise, add
            }

            prev = current;
        }

        return result;
    }

    public static void main(String[] args) {
        String roman = "MCMXCIV"; // 1994
        System.out.println("Integer value: " + romanToInt(roman));
    }
}
```

---

### 🔍 Example Inputs & Outputs:

| Roman   | Output |
| ------- | ------ |
| III     | 3      |
| IV      | 4      |
| IX      | 9      |
| LVIII   | 58     |
| MCMXCIV | 1994   |
