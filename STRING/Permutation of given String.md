# 📘 1. Backtracking with `used[]` 

### 🔹 Idea

* Use a **boolean\[] used** array to track which characters are already chosen.
* At each recursion step, try every unused character.
* Use a **HashSet** (or check conditionally) to avoid duplicates.
* When the permutation is complete, add it to the result list.

### 🔹 Complexity

* **Time:** `O(n * n!)` (each permutation generation costs O(n)).
* **Space:** `O(n)` recursion stack + `O(n)` for used\[].

### 🔹 Code

```java
class Solution {
    public ArrayList<String> findPermutation(String s) {
        ArrayList<String> res = new ArrayList<>();
        boolean[] used = new boolean[s.length()];
        char[] chars = s.toCharArray();
        Arrays.sort(chars); // sort to handle duplicates
        backtrack(chars, new StringBuilder(), used, res);
        return res;
    }

    private void backtrack(char[] chars, StringBuilder path, boolean[] used, ArrayList<String> res) {
        if (path.length() == chars.length) {
            res.add(path.toString());
            return;
        }

        for (int i = 0; i < chars.length; i++) {
            // skip duplicates
            if (used[i] || (i > 0 && chars[i] == chars[i - 1] && !used[i - 1])) continue;

            used[i] = true;
            path.append(chars[i]);
            backtrack(chars, path, used, res);
            path.deleteCharAt(path.length() - 1);
            used[i] = false;
        }
    }
}
```

---

# 📘 2. Swap-Based Recursion 

### 🔹 Idea

* Convert string into a **char array**.
* Recursively swap each character with the current index.
* After recursion, **swap back** to restore state (backtracking).
* Use a **HashSet** or conditional check to skip duplicates.

### 🔹 Complexity

* **Time:** `O(n * n!)`
* **Space:** `O(n)` recursion stack.
* More memory-efficient (no extra boolean\[]).

### 🔹 Code

```java
class Solution {
    public ArrayList<String> findPermutation(String s) {
        ArrayList<String> res = new ArrayList<>();
        char[] arr = s.toCharArray();
        Arrays.sort(arr); // sort to handle duplicates
        permute(arr, 0, res);
        return res;
    }

    private void permute(char[] arr, int index, ArrayList<String> res) {
        if (index == arr.length) {
            res.add(new String(arr));
            return;
        }

        HashSet<Character> seen = new HashSet<>();
        for (int i = index; i < arr.length; i++) {
            if (seen.contains(arr[i])) continue; // skip duplicates
            seen.add(arr[i]);

            swap(arr, i, index);
            permute(arr, index + 1, res);
            swap(arr, i, index); // backtrack
        }
    }

    private void swap(char[] arr, int i, int j) {
        char temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}
```

---

## ✅ When to Use

* **Backtracking with used\[]** → Best for **teaching, clarity, and handling duplicates explicitly**.
* **Swap-based recursion** → Best for **interviews, clean code, and efficiency**.

