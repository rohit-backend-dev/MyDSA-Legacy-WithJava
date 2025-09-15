
## 🔹 What is `StringBuilder`?

* A **mutable sequence of characters** (unlike `String` which is immutable).
* Belongs to `java.lang` package.
* Faster than `StringBuffer` (because it is **not synchronized**).
* Used when we need to perform **lots of modifications** (append, insert, delete, reverse, etc.) on strings.

👉 Declaration:

```java
StringBuilder sb = new StringBuilder("Hello");
```

---

## 🔹 Common Constructors

```java
StringBuilder()                 // creates empty builder with capacity 16
StringBuilder(String str)       // creates builder with given string
StringBuilder(int capacity)     // creates empty builder with given capacity
```

---

## 🔹 Predefined Methods of `StringBuilder`

### 1. `append(...)`

Adds text to the end.

```java
StringBuilder sb = new StringBuilder("Java");
sb.append(" Rocks");
System.out.println(sb);  // Java Rocks
```

---

### 2. `insert(int index, ...)`

Inserts text at specified index.

```java
sb.insert(4, " Programming");
System.out.println(sb);  // Java Programming Rocks
```

---

### 3. `replace(int start, int end, String str)`

Replaces characters from `start` to `end-1`.

```java
sb.replace(0, 4, "Python");
System.out.println(sb);  // Python Programming Rocks
```

---

### 4. `delete(int start, int end)`

Deletes characters from `start` to `end-1`.

```java
sb.delete(0, 7);
System.out.println(sb);  // Programming Rocks
```

---

### 5. `deleteCharAt(int index)`

Deletes one character at the given index.

```java
sb.deleteCharAt(0);
System.out.println(sb);  // rogramming Rocks
```

---

### 6. `reverse()`

Reverses the sequence.

```java
sb.reverse();
System.out.println(sb);  // skcoR gnimmargorP
```

---

### 7. `capacity()`

Returns the current capacity (default 16 + string length).

```java
System.out.println(sb.capacity());
```

---

### 8. `length()`

Returns number of characters in the sequence.

```java
System.out.println(sb.length());
```

---

### 9. `charAt(int index)`

Returns the character at a given index.

```java
System.out.println(sb.charAt(2));
```

---

### 10. `setCharAt(int index, char ch)`

Changes a character at the given index.

```java
sb.setCharAt(0, 'J');
System.out.println(sb);
```

---

### 11. `substring(int start)`

Extracts substring from `start` till end.

```java
System.out.println(sb.substring(5));
```

### 12. `substring(int start, int end)`

Extracts substring from `start` to `end-1`.

```java
System.out.println(sb.substring(0, 4));
```

---

### 13. `ensureCapacity(int minimumCapacity)`

Ensures capacity is at least given value.

---

### 14. `trimToSize()`

Reduces capacity to the current length.

---

### 15. `indexOf(String str)`

Finds first index of substring.

### 16. `lastIndexOf(String str)`

Finds last index of substring.

---

## 🔹 Example Program

```java
public class Main {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder("Hello");

        sb.append(" World");
        sb.insert(6, "Java ");
        sb.replace(0, 5, "Hi");
        sb.delete(2, 6);
        sb.reverse();

        System.out.println(sb);  // dlroW avaJ iH
    }
}
```
