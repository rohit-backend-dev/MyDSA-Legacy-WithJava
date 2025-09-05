

# 📘 Reverse an Array & Reverse a String (Two-Pointer Approach)

## 🔹 1. Reverse an Array

**Problem:**
[Reverse an Array – GFG](https://www.geeksforgeeks.org/problems/reverse-an-array/1)

**Approach:**

* Use **two pointers** (`i` at start, `j` at end).
* Swap elements at `i` and `j`.
* Move `i++` (forward) and `j--` (backward) until `i >= j`.

**Java Code:**

```java
class Solution {
    public void reverseArray(int arr[]) {
        int i = 0;
        int j = arr.length - 1;
        
        while (i < j) {
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
            
            i++;
            j--;
        }
    } 
}
```

**Time Complexity:** `O(n)`
**Space Complexity:** `O(1)` (in-place)

---

## 🔹 2. Reverse a String

**Problem:**
[Reverse a String – GFG](https://www.geeksforgeeks.org/problems/reverse-a-string/1)

**Approach:**

* Since **Strings in Java are immutable**, convert it into a `char[]`.
* Apply the same **two-pointer swapping logic**.
* Convert the reversed `char[]` back into a `String`.

**Java Code:**

```java
class Solution {
    public static String reverseString(String s) {
        char[] arr = s.toCharArray();
        int i = 0, j = arr.length - 1;
        
        while (i < j) {
            char temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
            
            i++;
            j--;
        }
        
        return new String(arr);
    }
}
```

**Time Complexity:** `O(n)`
**Space Complexity:** `O(n)` (extra char array, unavoidable due to immutability)

---


👉 Do you want me to make a **combined PDF/Word file (well formatted with explanations + code)** for your placement prep notes?
