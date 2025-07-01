# 🚀 Top 20 DSA Coding Patterns: Explanations & Roadmap

Here's a curated roadmap for the 20 most important coding patterns you must master to crack DSA interviews at top companies (Google, Amazon, Microsoft, Meta, etc.). Instead of just listing problems, this guide explains each pattern, when to use it, and how to master it—so you can recognize and apply them in any coding round.

---

## ✅ Core 20 DSA Coding Patterns (with Explanations)

---

### 1. 🔁 Two Pointers

**What:** Use two indices moving through an array/string to scan, partition, compare, or modify data.

**When:** Sorted arrays, searching for pairs, removing duplicates, reversing, palindromes.

**How to Master:**
- Practice moving both pointers towards/away from each other.
- Focus on array/string problems that require O(1) space.
- Common forms: opposite ends (start/end), same direction (start/fast), slow/fast.

**Roadmap:** 
- Start with finding pairs/triplets with a given sum.
- Try palindrome checks and array modifications in-place.

---

### 2. 📦 Sliding Window

**What:** Process a subarray/subsequence of fixed/variable length as a "window," moving it step by step.

**When:** Maximum/minimum of subarrays, longest/shortest substring, frequency/counting in a window.

**How to Master:**
- Learn fixed vs. variable window problems.
- Focus on maintaining window state efficiently (sum, set, map).
- Practice problems with window size K and dynamic resizing.

**Roadmap:**
- Begin with fixed-size windows, then move to dynamic ones (longest substring/unique).

---

### 3. 🐢 Fast & Slow Pointers (Tortoise & Hare)

**What:** Use two pointers at different speeds to detect cycles or find midpoints.

**When:** Cycle detection in linked lists, finding the middle element, duplicate finding.

**How to Master:**
- Understand the principle: if there's a loop, fast and slow will meet.
- Practice with linked lists, arrays, and number sequences.

**Roadmap:**
- Cycle detection variants, then finding mid-point or entry-point of cycle.

---

### 4. 🧱 Merge Intervals

**What:** Sort and merge overlapping intervals into one.

**When:** Calendar merging, scheduling, range consolidation.

**How to Master:**
- Practice sorting by start time, merging by comparing end/start.
- Learn to handle edge cases (touching, nested, separate intervals).

**Roadmap:**
- Start with merging, then insertion, then coverage/counting overlapping intervals.

---

### 5. 🔄 Cyclic Sort

**What:** Place each number at its correct index when range is known (e.g., 1 to N).

**When:** Find missing/duplicate numbers, organize small-range arrays.

**How to Master:**
- Learn to swap numbers in place until each is at its "home."
- Apply on problems with constraints: numbers from 1–N, unique/missing/duplicates.

**Roadmap:**
- First, organize array, then adapt to find missing/duplicate values.

---

### 6. 🔃 In-place Linked List Reversal

**What:** Reverse all or part of a linked list using pointer manipulation, in-place.

**When:** Full/partial reversal, k-group reversal, palindrome check in lists.

**How to Master:**
- Practice both iterative and recursive reversal.
- Understand pointer updates and breaking/reconnecting nodes.

**Roadmap:**
- Start with complete reversal, then move to sublist/k-group reversal and reordering.

---

### 7. 🌳 Tree BFS (Level Order Traversal)

**What:** Traverse a tree level by level (breadth-first), using a queue.

**When:** Finding depth, levels, zigzag/spiral order, or right-side view.

**How to Master:**
- Implement BFS with a queue.
- Modify traversal for various outputs: depth, specific levels, alternations.

**Roadmap:**
- Level order, then add variations (zigzag, view, sum at levels).

---

### 8. 🌲 Tree DFS (Recursive & Iterative)

**What:** Traverse tree deeply via preorder, inorder, postorder.

**When:** Path finding, subtree checks, calculating sums/depths.

**How to Master:**
- Practice all three DFS orders (recursive and iterative).
- Learn to pass/accumulate info during traversal (depth, path, sum).

**Roadmap:**
- Start with traversals, then path-finding, subtree/ancestor/descendant queries.

---

### 9. 🥄 Two Heaps

**What:** Use a min-heap & max-heap to balance k-largest/k-smallest, or median.

**When:** Streaming median, k-th smallest/largest, balancing elements.

**How to Master:**
- Learn to add/remove elements from heaps while keeping them balanced.
- Practice with ongoing streams and fixed-size windows.

**Roadmap:**
- Find median, then tackle k-th elements and merging data streams.

---

### 10. 🔢 Subsets & Backtracking

**What:** Recursively generate all subsets, permutations, or valid combinations.

**When:** Combinatorial generation, N-Queens, word search, subset sum.

**How to Master:**
- Practice recursive tree of decisions: include/exclude, choose/skip.
- Learn pruning and backtracking to avoid unnecessary paths.

**Roadmap:**
- Start with subset generation, then permutations/combinations, then constraint-based (e.g., N-Queens).

---

### 11. 🔍 Modified Binary Search

**What:** Adapt binary search for rotated/special arrays, grids, or finding boundaries.

**When:** Rotated arrays, peak finding, searching ranges/positions.

**How to Master:**
- Understand standard binary search, then apply on rotated/shifted cases.
- Learn to search for first/last occurrence, peaks, boundaries.

**Roadmap:**
- Basic search, then rotated/mountain/2D grid cases.

---

### 12. 🏆 Top K Elements (Heap-based)

**What:** Use a heap (priority queue) to find k largest/smallest/frequent items.

**When:** Sorting top-k, frequency analysis, leaderboard problems.

**How to Master:**
- Learn heap operations and efficient extraction.
- Practice frequency counts and custom sorting.

**Roadmap:**
- K-largest/smallest, top-k frequent, then more complex frequency ordering.

---

### 13. 🧵 K-way Merge

**What:** Merge k sorted arrays/lists efficiently via a min-heap.

**When:** Merging logs, streams, lists, arrays.

**How to Master:**
- Implement merging with a heap for k-way data.
- Practice with both arrays and linked lists.

**Roadmap:**
- Begin with two lists, scale up to k, then range/median in merged data.

---

### 14. 🎒 0/1 Knapsack (DP)

**What:** Dynamic programming for subset selection, maximizing/minimizing value under constraints.

**When:** Subset sum, resource allocation, partition problems.

**How to Master:**
- Build DP tables for inclusion/exclusion.
- Practice both recursive (with memoization) and tabular DP.

**Roadmap:**
- Subset sum, knapsack, then partition and variations with extra constraints.

---

### 15. 🔁 Topological Sort (Graph + In-Degree)

**What:** Order tasks/nodes in a DAG respecting dependencies.

**When:** Scheduling, course prerequisites, build systems.

**How to Master:**
- Implement Kahn’s algorithm (BFS with in-degree).
- Detect cycles and handle multiple valid orders.

**Roadmap:**
- Basic ordering, then complex dependency graphs and cycles.

---

### 16. 🔄 Floyd's Cycle Detection

**What:** Detect cycles in linked lists/arrays with fast-slow pointers.

**When:** Linked list cycles, happy number, repeated states.

**How to Master:**
- Practice Tortoise and Hare algorithm in various contexts.
- Adapt for both list and number problems.

**Roadmap:**
- Cycle detection, then starting point/location of cycles.

---

### 17. 📈 Kadane’s Algorithm (Max Subarray Sum)

**What:** Dynamic approach to find max sum subarray in linear time.

**When:** Max/min subarray sums, product variants, circular arrays.

**How to Master:**
- Understand maintaining current/max sum while iterating.
- Practice plain arrays, then circular and product variants.

**Roadmap:**
- Start with max sum, then expand to products and circular subarrays.

---

### 18. 🧬 LCS / LCS-based (Dynamic Programming)

**What:** Find longest common subsequence/substring, edit distance, palindromic subsequence.

**When:** String comparison, diff tools, DNA/protein alignment.

**How to Master:**
- Build DP tables/recursion with memoization for edit distance, subsequences.
- Modify for palindrome, distinct subsequences, etc.

**Roadmap:**
- LCS, edit distance, palindromic variations, then count-based subsequences.

---

### 19. 🔗 Union Find (Disjoint Set)

**What:** Group elements, check connectivity, or detect cycles efficiently.

**When:** Connected components, network queries, friend circles.

**How to Master:**
- Implement union by rank and path compression.
- Practice with graphs and dynamic connectivity.

**Roadmap:**
- Find/connect, then cycle detection and grouping.

---

### 20. 🔡 Trie (Prefix Tree)

**What:** Tree structure for fast prefix search, autocomplete, and dictionary queries.

**When:** Word search, autocomplete, spell-check, prefix grouping.

**How to Master:**
- Implement insert/search.
- Practice with prefix, word suggestions, replacement.

**Roadmap:**
- Simple word insert/search, then prefix queries, then advanced (replace, suggestions).

---

## 🎯 Bonus Patterns

| Pattern                  | Use Case Example                       |
|--------------------------|----------------------------------------|
| Monotonic Stack          | Next Greater Element, Histogram Area   |
| Prefix Sum / Diff        | Range sum queries                      |
| Binary Search on Answer  | Minimize/maximize under constraint     |
| Matrix Graph BFS/DFS     | Number of Islands, Surrounded Regions  |
| Bitmasking               | Subsets, DP optimization               |

---

# 💎 Roadmap to Mastery

1. **Stick to Patterns:** Dedicate 2–3 days per pattern for focused learning.
2. **Progress Gradually:** Solve 2 easy, 3 medium, 1 hard for each pattern.
3. **Explain Aloud:** Teach your solution—clarifies logic and communication.
4. **Track Progress:** Maintain a logbook—pattern, problem, difficulty, time, notes.
5. **Solve From Scratch:** Code without peeking, then review solutions.
6. **Handle Edge Cases:** Think about constraints, maps/sets, sorting, etc.
7. **Mock Interviews:** Simulate timed, real-world scenarios.
8. **Spaced Revision:** Review and re-solve every 7–10 days.
9. **Understand, Don’t Memorize:** Focus on deep mastery.
10. **Apply to Real Problems:** Use InterviewBit, CodeStudio, GFG, Striver’s Sheet.

---

# 🏁 Final Summary

- **Focus on patterns, not just topics.**
- **Practice deep, not just hard.**
- **Understand, then memorize.**
- **Stay consistent and track your growth.**

---
