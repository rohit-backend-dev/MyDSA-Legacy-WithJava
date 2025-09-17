
### 🔹 1. Left Rotate

Example:
`s = "abcdef", k = 2` → `"cdefab"`

👉 We cut the string into two parts:

* from `0` to `k-1`
* from `k` to `end`
  Then append in swapped order.

```java
class Solution {
    // Left rotation by k
    public String leftRotate(String s, int k) {
        int n = s.length();
        k = k % n;  // handle k > n
        return s.substring(k) + s.substring(0, k);
    }
}
```

---

### 🔹 2. Right Rotate

Example:
`s = "abcdef", k = 2` → `"efabcd"`

👉 Right rotation by `k` = Left rotation by `n - k`.

```java
class Solution {
    // Right rotation by k
    public String rightRotate(String s, int k) {
        int n = s.length();
        k = k % n;  // handle k > n
        return s.substring(n - k) + s.substring(0, n - k);
    }
}
```

---

### 🔹 3. Combined Version

Single method for both directions:

```java
class Solution {
    public String rotate(String s, int k, boolean left) {
        int n = s.length();
        k = k % n;
        
        if (left) {
            return s.substring(k) + s.substring(0, k);   // left rotation
        } else {
            return s.substring(n - k) + s.substring(0, n - k); // right rotation
        }
    }
}
```

---

✅ **Time Complexity:** `O(n)`
✅ **Space Complexity:** `O(1)` (apart from new string object)

