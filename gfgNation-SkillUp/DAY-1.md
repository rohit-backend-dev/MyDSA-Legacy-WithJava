# Divisible by 13 in Java: Multiple Approaches

This document presents several ways to check if a given string of digits is divisible by 13 in Java, suitable for both small and very large numbers.

---

## 1. BigInteger Method (Best for Simplicity and Large Numbers)

```java
import java.math.BigInteger;

class GfG {
    static boolean divBy13(String s) {
        BigInteger num = new BigInteger(s);
        return num.mod(BigInteger.valueOf(13)).equals(BigInteger.ZERO);
    }

    public static void main(String[] args) {
        String s = "2911285";
        System.out.println(divBy13(s));
    }
}
```

**Pros:**

- Super clean and minimal code.
- Safely handles very large numbers without overflow.

**Cons:**

- Slightly more overhead due to the use of `BigInteger`.

---

## 2. Character ASCII-Free Approach (Using `Character.getNumericValue()`)

```java
class GfG {
    static boolean divBy13(String s) {
        int rem = 0;
        for (char c : s.toCharArray()) {
            rem = (rem * 10 + Character.getNumericValue(c)) % 13;
        }
        return rem == 0;
    }

    public static void main(String[] args) {
        String s = "2911285";
        System.out.println(divBy13(s));
    }
}
```

**Pros:**

- Efficient for interviews and competitive programming.
- Avoids `BigInteger` and prevents overflow using remainder logic.
- Cleaner handling of characters using `Character.getNumericValue()`.

**Cons:**

- Logic is similar to modulus approach but uses a semantic method for digits.

---

## 3. Traditional Way Using `Long.parseLong()` (Only if within Long Range)

```java
class GfG {
    static boolean divBy13(String s) {
        long number = Long.parseLong(s);
        return number % 13 == 0;
    }

    public static void main(String[] args) {
        String s = "2911285";
        System.out.println(divBy13(s));
    }
}
```

**Pros:**

- Straightforward and simple code.
- Good when the number can comfortably fit within the range of `long` (up to ~18 digits).

**Cons:**

- Risk of overflow for very large numbers (not suitable for strings with more than 18 digits).

---



**Happy Coding! 🚀**
