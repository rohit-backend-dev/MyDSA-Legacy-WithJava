## 1. 🔑 Core String Concepts

Think of a string as a **character array with extra features**.

* **Immutable (in Java):**

  * Once created, a `String` cannot be modified.
  * Operations like `s += "a"` create a **new object**.
  * For mutable strings → use `StringBuilder` / `StringBuffer`.

* **Conversions:**

  ```java
  char[] arr = s.toCharArray();   // string → char array
  String str = new String(arr);   // char array → string
  int num = Integer.parseInt("123"); // string → int
  String s = String.valueOf(123); // int → string
  ```

* **Important methods:**
  ```
   s.length();                  // returns the number of characters in the string
  s.charAt(i);                 // returns the character at index i (0-based)
  s.substring(l, r);           // returns substring from index l (inclusive) to r (exclusive)
  s.indexOf("ab");             // returns the first index where "ab" occurs, -1 if not found
  s.equals("abc");             // compares content of string with "abc", returns true/false
  s.toLowerCase();             // converts all characters to lowercase
  s.toUpperCase();             // converts all characters to uppercase
  s.trim();                    // removes leading and trailing spaces
  s.replace('a','b');          // replaces all 'a' with 'b' in the string
```

* **Comparison:**

  * `==` → checks **reference** (same object in memory).
  * `.equals()` → checks **content**.

---

## 2. ⚙️ Techniques in String DSA

These are the main patterns you’ll see in interviews:

### (a) Two Pointers

* Used for **palindrome check**, **reverse string**, **remove duplicates**, etc.
* Example:

  ```java
  int l = 0, r = s.length()-1;
  while(l < r) {
      if(s.charAt(l) != s.charAt(r)) return false;
      l++; r--;
  }
  ```

### (b) Frequency Count (HashMap / Array)

* Used for **anagrams, character counts, first unique char**.
* Example:

  ```java
  int[] freq = new int[26];
  for(char c: s.toCharArray()) freq[c-'a']++;
  ```

### (c) Sliding Window

* Used for **longest substring without repeating characters, longest repeating char replacement**.
* Example:

  ```java
  int l = 0;
  for (int r = 0; r < s.length(); r++) {
      // expand window
      // shrink window if invalid
      l++;
  }
  ```

### (d) String Builder

* Efficient for building strings (avoid repeated concatenation).
* Example: reverse words

  ```java
  StringBuilder sb = new StringBuilder(s);
  sb.reverse().toString();
  ```

### (e) Sorting

* Sorting helps in **anagrams** or **canonical form comparison**.
* Example:

  ```java
  char[] a = s.toCharArray();
  Arrays.sort(a);
  ```

* Example: "Find substring in a string" → `O(n)` instead of `O(n*m)`.

---
