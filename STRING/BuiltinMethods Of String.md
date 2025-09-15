
## **1. Creation & Conversion**

* `char[] toCharArray()` – Converts string to character array.
* `byte[] getBytes()` – Converts string to byte array.
* `String valueOf(...)` – Converts primitives or objects to string.
* `String.format(...)` – Returns formatted string.
* `String.join(delimiter, elements...)` – Joins strings with a delimiter.

---

## **2. Length & Character Access**

* `int length()` – Returns string length.
* `char charAt(int index)` – Returns character at index.
* `int codePointAt(int index)` – Unicode code point at index.
* `int codePointBefore(int index)` – Unicode code point before index.
* `int codePointCount(int beginIndex, int endIndex)` – Number of Unicode code points in range.
* `int indexOf(char/substring)` – First occurrence.
* `int lastIndexOf(char/substring)` – Last occurrence.

---

## **3. Comparison**

* `boolean equals(Object obj)` – Exact match.
* `boolean equalsIgnoreCase(String another)` – Case-insensitive match.
* `int compareTo(String another)` – Lexicographic comparison.
* `int compareToIgnoreCase(String another)` – Lexicographic ignoring case.
* `boolean contentEquals(CharSequence cs)` – Checks content equality.
* `boolean matches(String regex)` – Regex match.

---

## **4. Searching & Substring**

* `boolean contains(CharSequence s)` – Checks if substring exists.
* `boolean startsWith(String prefix)` – Checks prefix.
* `boolean endsWith(String suffix)` – Checks suffix.
* `String substring(int beginIndex)` – Returns substring from index.
* `String substring(int beginIndex, int endIndex)` – Returns substring in range.
* `String replace(char oldChar, char newChar)` – Replace characters.
* `String replace(CharSequence target, CharSequence replacement)` – Replace substring.
* `String replaceAll(String regex, String replacement)` – Replace by regex.
* `String replaceFirst(String regex, String replacement)` – Replace first match by regex.
* `String[] split(String regex)` – Split string by regex.
* `String[] split(String regex, int limit)` – Split with limit.

---

## **5. Case & Whitespace**

* `String toLowerCase()` – Lowercase.
* `String toLowerCase(Locale locale)` – Locale-specific lowercase.
* `String toUpperCase()` – Uppercase.
* `String toUpperCase(Locale locale)` – Locale-specific uppercase.
* `String trim()` – Remove leading/trailing spaces.
* `String strip()` – Java 11+, removes leading/trailing whitespace.
* `String stripLeading()` – Remove leading whitespace.
* `String stripTrailing()` – Remove trailing whitespace.
* `boolean isEmpty()` – Check if string is empty (`length() == 0`).
* `boolean isBlank()` – Java 11+, check if string is empty or whitespace.

---

## **6. Conversion & Joining**

* `String concat(String str)` – Concatenate string.
* `char[] toCharArray()` – Convert to char array.
* `byte[] getBytes()` – Convert to byte array.
* `String intern()` – Returns string from pool if already exists.
* `static String join(CharSequence delimiter, CharSequence... elements)` – Join strings.

---

## **7. Formatting & Value Conversion**

* `static String format(String format, Object... args)` – Create formatted string.
* `static String valueOf(int i / double d / Object o / boolean b / char c)` – Converts value to string.

---

## **8. Content Checking (Java 11+)**

* `boolean isBlank()` – Only whitespace or empty.
* `boolean lines()` – Stream of lines in string.
* `String repeat(int count)` – Repeat string `count` times.
* `boolean strip().isEmpty()` – Combination to check empty after strip.

---

## **9. Miscellaneous**

* `StringBuilder` & `StringBuffer` are mutable alternatives with additional methods:

  * `append()`, `insert()`, `delete()`, `reverse()`, `replace()`, `charAt()`, `setCharAt()`, `length()`, etc.

