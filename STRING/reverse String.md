1. When the input is a **`char[]`**
2. When the input is a **`String`**

---

## ✅ Case 1: Reverse a `char[]`

This is exactly what LeetCode asks (problem 344).

### 🔹 Optimal (two-pointer, in-place)

```java
class Solution {
    public void reverseString(char[] s) {
        int left = 0, right = s.length - 1;

        while (left < right) {
            char temp = s[left];
            s[left] = s[right];
            s[right] = temp;
            left++;
            right--;
        }
    }
}
```

### 🔎 Example

Input: `['h','e','l','l','o']`
Output: `['o','l','l','e','h']`

---

## ✅ Case 2: Reverse a `String`

Since `String` in Java is **immutable**, you cannot swap characters directly. You need to either:

* Convert to `char[]`, or
* Use `StringBuilder`.

### 🔹 Using `StringBuilder` (one-liner)

```java
class Solution {
    public String reverseString(String s) {
        return new StringBuilder(s).reverse().toString();
    }
}
```

### 🔹 Using char array (manual swap)

```java
class Solution {
    public String reverseString(String s) {
        char[] arr = s.toCharArray();
        int left = 0, right = arr.length - 1;

        while (left < right) {
            char temp = arr[left];
            arr[left] = arr[right];
            arr[right] = temp;
            left++;
            right--;
        }
        return new String(arr);
    }
}
```

---

## ⚖️ Summary

* **Input as `char[]` → reverse in-place (two-pointer).**
* **Input as `String` → either use `StringBuilder.reverse()` or convert to `char[]` and apply two-pointer.**

