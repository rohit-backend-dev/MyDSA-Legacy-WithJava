# Asked in *step2gen* technology

# 📝 Problem: Filter Words by Prime ASCII Sum

### Problem Statement

You are given an array of strings `words`.
For each word:

1. Take the **first** and **last** character.
2. Compute their **ASCII values** and add them.
3. If the sum is a **prime number**, remove the word.
4. Otherwise, keep it.

Return the list of words after applying the above filtering.

---

### Example 1

```
Input: words = ["Apple", "dog", "cat", "Fox"]
Output: ["Apple", "dog", "cat", "Fox"]

Explanation:
- "Apple" → 'A'(65) + 'e'(101) = 166 → not prime → keep
- "dog"   → 'd'(100) + 'g'(103) = 203 → not prime → keep
- "cat"   → 'c'(99) + 't'(116) = 215 → not prime → keep
- "Fox"   → 'F'(70) + 'x'(120) = 190 → not prime → keep
So, no word is removed.
```

---

### Example 2

```
Input: words = ["ace", "bee", "dad", "top"]
Output: ["ace", "dad", "top"]

Explanation:
- "ace" → 'a'(97) + 'e'(101) = 198 → not prime → keep
- "bee" → 'b'(98) + 'e'(101) = 199 → prime → remove
- "dad" → 'd'(100) + 'd'(100) = 200 → not prime → keep
- "top" → 't'(116) + 'p'(112) = 228 → not prime → keep

After filtering: ["ace", "dad", "top"]
```

---

### Constraints

* `1 <= words.length <= 10^4`
* `1 <= words[i].length <= 100`
* Words consist of uppercase and lowercase English letters.

---

### Intuition

* We only need **first and last characters** of each word.
* Their ASCII sum is at most `122 + 122 = 244`.
* Prime check is cheap (`O(√n)` ≈ constant).
* So the entire algorithm runs in **O(m)** where `m = number of words`.

---

### Efficient Solution (Java)

```java
import java.util.*;

class Solution {
    public List<String> filterWords(String[] words) {
        List<String> result = new ArrayList<>();
        
        for (String word : words) {
            char first = word.charAt(0);
            char last = word.charAt(word.length() - 1);
            int sum = first + last;
            
            if (!isPrime(sum)) {
                result.add(word);
            }
        }
        return result;
    }
    
    private boolean isPrime(int n) {
        if (n < 2) return false;
        if (n % 2 == 0) return n == 2;
        for (int i = 3; i * i <= n; i += 2) {
            if (n % i == 0) return false;
        }
        return true;
    }

    public static void main(String[] args) {
        Solution sol = new Solution();
        String[] words1 = {"Apple", "dog", "cat", "Fox"};
        System.out.println(sol.filterWords(words1)); 
        // Output: [Apple, dog, cat, Fox]

        String[] words2 = {"ace", "bee", "dad", "top"};
        System.out.println(sol.filterWords(words2)); 
        // Output: [ace, dad, top]
    }
}
```

---

### Complexity Analysis

* **Prime check**: `O(√244)` ≈ constant.
* **For m words**: `O(m)`.
* **Space**: `O(1)` extra (besides output).

