```java
class Solution {
    public boolean isValid(String s) {
        
        Stack<Character> st = new Stack<>(); 
  
        for (char c : s.toCharArray()) {
            // 1. If it's an opening bracket, push to stack
            if (c == '(' || c == '{' || c == '[') {
                st.push(c);
            } 
            // 2. If it's a closing bracket
            else {
                if (st.isEmpty()) return false; // no opening bracket for this closing one
                
                char top = st.pop(); // get the last opened bracket

                // 3. Check if closing matches opening
                if ((c == ')' && top != '(') ||
                    (c == '}' && top != '{') ||
                    (c == ']' && top != '[')) {
                    return false; // wrong type of bracket
                }
            }
        }
  
        // 4. In the end, stack must be empty (all opened are closed)
        return st.isEmpty();
    }
}
```

---

## 🔹 Dry Run Examples

### Example 1: `"()[]{}"`

* `(` → push → stack: `(`
* `)` → pop `(` → matches → ✅
* `[` → push → stack: `[`
* `]` → pop `[` → matches → ✅
* `{` → push → stack: `{`
* `}` → pop `{` → matches → ✅
* End → stack empty → return `true`

---

### Example 2: `"([)]"`

* `(` → push → stack: `(`
* `[` → push → stack: `(` `[`
* `)` → pop `[` → mismatch (`)` ≠ `[`) → return `false`

---

### Example 3: `"(("`

* `(` → push → stack: `(`
* `(` → push → stack: `(` `(`
* End → stack not empty → return `false`

---

## 🔹 Complexity

* **Time:** O(n) → every character processed once.
* **Space:** O(n) → in worst case, all characters are opening brackets.

