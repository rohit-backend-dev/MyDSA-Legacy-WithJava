-

## 🔹 Method 1: Using `if–else` (Greedy Subtraction)

```java
class Solution {
    public String intToRoman(int num) {
        StringBuilder sb = new StringBuilder();

        while (num > 0) {
            if (num >= 1000) {
                sb.append("M");
                num -= 1000;
            } else if (num >= 900) {
                sb.append("CM");
                num -= 900;
            } else if (num >= 500) {
                sb.append("D");
                num -= 500;
            } else if (num >= 400) {
                sb.append("CD");
                num -= 400;
            } else if (num >= 100) {
                sb.append("C");
                num -= 100;
            } else if (num >= 90) {
                sb.append("XC");
                num -= 90;
            } else if (num >= 50) {
                sb.append("L");
                num -= 50;
            } else if (num >= 40) {
                sb.append("XL");
                num -= 40;
            } else if (num >= 10) {
                sb.append("X");
                num -= 10;
            } else if (num >= 9) {
                sb.append("IX");
                num -= 9;
            } else if (num >= 5) {
                sb.append("V");
                num -= 5;
            } else if (num >= 4) {
                sb.append("IV");
                num -= 4;
            } else {
                sb.append("I");
                num -= 1;
            }
        }

        return sb.toString();
    }
}
```

### ✅ Explanation

* Keep subtracting the **largest possible Roman value** from `num`.
* Append the corresponding Roman numeral each time.
* Repeat until `num == 0`.

**Example:**
`1994 → M (1000) + CM (900) + XC (90) + IV (4) = "MCMXCIV"`

---

## 🔹 Method 2: Using Value–Symbol Arrays (Greedy Loop)

```java
class Solution {
    public String intToRoman(int num) {
        // Value-symbol pairs from largest to smallest, including subtractive forms.
        int[] vals =    {1000, 900, 500, 400, 100,  90,  50,  40,  10,   9,   5,   4,   1};
        String[] syms = {"M",  "CM","D", "CD", "C", "XC", "L", "XL", "X",  "IX", "V", "IV", "I"};
        
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < vals.length && num > 0; i++) {
            int count = num / vals[i];   // how many times this value fits
            num %= vals[i];              // reduce num
            while (count-- > 0) sb.append(syms[i]); // append symbols
        }
        return sb.toString();
    }
}
```

### ✅ Explanation

* Store Roman numeral values and symbols in arrays.
* Loop through them in descending order.
* For each, calculate how many times it fits into `num`.
* Append that many symbols, subtract the value, and move to the next.

**Example:**
`58 → L (50) + VIII (8) = "LVIII"`

