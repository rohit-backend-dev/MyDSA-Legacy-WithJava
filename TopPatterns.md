# 🚀 Top 20 DSA Coding Patterns to Crack Any Interview

Here's a curated list of the most important and high-impact coding patterns—the core 20 patterns you should master first to confidently crack any DSA coding round, including top companies like Google, Amazon, Microsoft, Meta, etc.

---

## ✅ Core 20 DSA Coding Patterns

For each pattern, you'll find:
- **3 Must-Solve LeetCode Questions** (absolute essentials)
- **2 Practice LeetCode Questions** (to deepen mastery)
- **Additional Classic Questions** (from top DSA question banks for deep practice)

---

### 1. 🔁 Two Pointers

**Explanation:**  
Move two pointers (start, end) through an array or string to find pairs, reverse in-place, or partition data. Essential for problems on sorted arrays, palindrome checks, removing duplicates, and subarray searches.

**3 Must-Solve:**
- [Two Sum II - Input array is sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)
- [3Sum](https://leetcode.com/problems/3sum/)
- [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)

**2 Practice:**
- [Reverse String](https://leetcode.com/problems/reverse-string/)
- [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

**Classic Questions:**
- Reverse an Array/String [Article](https://www.geeksforgeeks.org/write-a-program-to-reverse-an-array-or-string/) [Practice](https://practice.geeksforgeeks.org/problems/reverse-an-array/0)
- Find the maximum and minimum element in an array [Article](https://www.geeksforgeeks.org/maximum-and-minimum-in-an-array/) [Practice](https://practice.geeksforgeeks.org/problems/find-minimum-and-maximum-element-in-an-array4428/1)
- Move all the negative elements to one side of the array [Article](https://www.geeksforgeeks.org/move-negative-numbers-beginning-positive-end-constant-extra-space/) [Practice](https://practice.geeksforgeeks.org/problems/move-all-negative-elements-to-end1813/1)
- Find all pairs on integer array whose sum is equal to given number [Article](https://www.geeksforgeeks.org/find-a-pair-with-the-given-sum-in-the-array/) [Practice](https://practice.geeksforgeeks.org/problems/count-pairs-with-given-sum5022/1)
- Rearrange the array in alternating positive and negative items with O(1) extra space [Article](https://www.geeksforgeeks.org/rearrange-array-alternating-positive-negative-items-o1-extra-space/) [Practice](https://practice.geeksforgeeks.org/problems/array-of-alternate-ve-and-ve-nos1401/1)
- Find if there is any subarray with sum equal to 0 [Article](https://www.geeksforgeeks.org/find-if-there-is-a-subarray-with-0-sum/) [Practice](https://practice.geeksforgeeks.org/problems/subarray-with-0-sum-1587115621/1)

---

### 2. 📦 Sliding Window

**Explanation:**  
Maintain a window (subarray or substring) to process a range of elements at a time. Ideal for finding maximum/minimum sums, longest substrings, or number of distinct elements.

**3 Must-Solve:**
- [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
- [Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)
- [Longest Substring with At Most K Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/)

**2 Practice:**
- [Maximum Sum Subarray of Size K](https://leetcode.com/problems/maximum-average-subarray-i/) (variation)
- [Permutation in String](https://leetcode.com/problems/permutation-in-string/)

**Classic Questions:**
- Smallest Subarray with sum greater than a given value [Article](https://www.geeksforgeeks.org/minimum-length-subarray-sum-greater-given-value/) [Practice](https://practice.geeksforgeeks.org/problems/smallest-subarray-with-sum-greater-than-x5651/1)
- First negative integer in every window of size “k” [Article](https://www.geeksforgeeks.org/first-negative-integer-every-window-size-k/) [Practice](https://practice.geeksforgeeks.org/problems/first-negative-integer-in-every-window-of-size-k3345/1)
- Sum of minimum and maximum elements of all subarrays of size “k” [Article](https://www.geeksforgeeks.org/sum-minimum-maximum-elements-subarrays-size-k/) [Practice](https://practice.geeksforgeeks.org/problems/sum-of-minimum-and-maximum-elements-of-all-subarrays-of-size-k3101/1)
- Maximum of all subarrays of size k [Article](https://www.geeksforgeeks.org/sliding-window-maximum-maximum-of-all-subarrays-of-size-k/) [Practice](https://practice.geeksforgeeks.org/problems/maximum-of-all-subarrays-of-size-k3101/1)

---

### 3. 🐢 Fast & Slow Pointers (Tortoise & Hare)

**Explanation:**  
Use two pointers moving at different speeds to detect cycles or find the middle of a list. Classic for cycle detection and mid-point finding in linked lists or number sequences.

**3 Must-Solve:**
- [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)
- [Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)
- [Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)

**2 Practice:**
- [Happy Number](https://leetcode.com/problems/happy-number/)
- [Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)

**Classic Questions:**
- Write a program to Detect loop in a linked list [Article](https://www.geeksforgeeks.org/detect-loop-in-a-linked-list/) [Practice](https://practice.geeksforgeeks.org/problems/detect-loop-in-linked-list/1)
- Write a program to Delete loop in a linked list [Article](https://www.geeksforgeeks.org/remove-loop-in-a-linked-list/) [Practice](https://practice.geeksforgeeks.org/problems/remove-loop-in-linked-list/1)
- Find the starting point of the loop [Article](https://www.geeksforgeeks.org/find-first-node-of-loop-in-a-linked-list/) [Practice](https://practice.geeksforgeeks.org/problems/find-first-node-of-loop-in-linked-list/1)
- Find the middle Element of a linked list [Article](https://www.geeksforgeeks.org/finding-middle-element-in-a-linked-list/) [Practice](https://practice.geeksforgeeks.org/problems/finding-middle-element-in-a-linked-list/1)
- Check if a linked list is a circular linked list [Article](https://www.geeksforgeeks.org/check-if-a-linked-list-is-circular-linked-list/) [Practice](https://practice.geeksforgeeks.org/problems/circular-linked-list/1)

---

### 4. 🧱 Merge Intervals

**Explanation:**  
Sort intervals and merge overlapping ones. Common in calendar event merging, range consolidation, and meeting room scheduling.

**3 Must-Solve:**
- [Merge Intervals](https://leetcode.com/problems/merge-intervals/)
- [Insert Interval](https://leetcode.com/problems/insert-interval/)
- [Meeting Rooms](https://leetcode.com/problems/meeting-rooms/)

**2 Practice:**
- [Employee Free Time](https://leetcode.com/problems/employee-free-time/)
- [Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/)

**Classic Questions:**
- Merge Overlapping Intervals [Article](https://www.geeksforgeeks.org/merging-intervals/) [Practice](https://practice.geeksforgeeks.org/problems/overlapping-intervals/0)
- Merge 2 sorted arrays without using Extra space [Article](https://www.geeksforgeeks.org/merge-two-sorted-arrays-o1-extra-space/) [Practice](https://practice.geeksforgeeks.org/problems/merge-two-sorted-arrays-1587115620/1)
- Merge 2 sorted arrays [Article](https://www.geeksforgeeks.org/merge-two-sorted-arrays/) [Practice](https://practice.geeksforgeeks.org/problems/merge-two-sorted-arrays-1587115620/1)
- Merge K Sorted Linked list [Article](https://www.geeksforgeeks.org/merge-k-sorted-linked-lists/) [Practice](https://practice.geeksforgeeks.org/problems/merge-k-sorted-linked-lists/1)
- Merge “K” sorted arrays [Article](https://www.geeksforgeeks.org/merge-k-sorted-arrays/) [Practice](https://practice.geeksforgeeks.org/problems/merge-k-sorted-arrays/1)

---

### 5. 🔄 Cyclic Sort

**Explanation:**  
Efficient for sorting arrays with numbers in a known range (1 to N). Used for finding missing/duplicate numbers and cycle-based placements.

**3 Must-Solve:**
- [Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)
- [Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)
- [First Missing Positive](https://leetcode.com/problems/first-missing-positive/)

**2 Practice:**
- [Find All Duplicates in an Array](https://leetcode.com/problems/find-all-duplicates-in-an-array/)
- [Missing Number](https://leetcode.com/problems/missing-number/)

**Classic Questions:**
- Write a program to cyclically rotate an array by one [Article](https://www.geeksforgeeks.org/c-program-cyclically-rotate-array-one/) [Practice](https://practice.geeksforgeeks.org/problems/cyclically-rotate-an-array-by-one2614/1)
- Given an array which consists of only 0, 1 and 2. Sort the array without using any sorting algo [Article](https://www.geeksforgeeks.org/sort-an-array-of-0s-1s-and-2s/) [Practice](https://practice.geeksforgeeks.org/problems/sort-an-array-of-0s-1s-and-2s/0)
- Count Inversion [Article](https://www.geeksforgeeks.org/counting-inversions/) [Practice](https://practice.geeksforgeeks.org/problems/inversion-of-array/0)
- Find the repeating and the missing [Article](https://www.geeksforgeeks.org/find-a-repeating-and-a-missing-number/) [Practice](https://practice.geeksforgeeks.org/problems/find-missing-and-repeating2512/1)

---

### 6. 🔃 In-place Linked List Reversal

**Explanation:**  
Reverse the entire linked list or a sublist in-place using pointer manipulation. Appears frequently in technical interviews.

**3 Must-Solve:**
- [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)
- [Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/)
- [Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)

**2 Practice:**
- [Reverse Linked List II](https://leetcode.com/problems/reverse-linked-list-ii/)
- [Reorder List](https://leetcode.com/problems/reorder-list/)

**Classic Questions:**
- Write a Program to reverse the Linked List. (Both Iterative and recursive) [Article](https://www.geeksforgeeks.org/reverse-a-linked-list/) [Practice](https://practice.geeksforgeeks.org/problems/reverse-a-linked-list/1)
- Reverse a Linked List in group of Given Size [Article](https://www.geeksforgeeks.org/reverse-a-list-in-groups-of-given-size/) [Practice](https://practice.geeksforgeeks.org/problems/reverse-a-linked-list-in-groups-of-given-size/1)
- Write a Program to Move the last element to Front in a Linked List [Article](https://www.geeksforgeeks.org/move-last-element-to-front-of-a-given-linked-list/) [Practice](https://practice.geeksforgeeks.org/problems/move-last-element-to-front-of-a-linked-list/1)
- Write a Program to check whether the Singly Linked list is a palindrome or not [Article](https://www.geeksforgeeks.org/function-to-check-if-a-singly-linked-list-is-palindrome/) [Practice](https://practice.geeksforgeeks.org/problems/check-if-linked-list-is-pallindrome/1)

---

### 7. 🌳 Tree BFS (Level Order Traversal)

**Explanation:**  
Traverse a tree level by level (breadth-first), typically using a queue. Useful for depth calculations, zigzag orders, and right-side views.

**3 Must-Solve:**
- [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)
- [Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/)
- [Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/)

**2 Practice:**
- [Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)
- [Populating Next Right Pointers in Each Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)

**Classic Questions:**
- Level order traversal [Article](https://www.geeksforgeeks.org/level-order-tree-traversal/) [Practice](https://practice.geeksforgeeks.org/problems/level-order-traversal/1)
- Reverse Level Order traversal [Article](https://www.geeksforgeeks.org/reverse-level-order-traversal/) [Practice](https://practice.geeksforgeeks.org/problems/reverse-level-order-traversal/1)
- Print elements in sorted order using row-column wise sorted matrix [Article](https://www.geeksforgeeks.org/print-elements-sorted-order-row-column-wise-sorted-matrix/) [Practice](https://practice.geeksforgeeks.org/problems/sorted-matrix/0)

---

### 8. 🌲 Tree DFS (Recursive & Iterative)

**Explanation:**  
Traverse a tree deeply (preorder, inorder, postorder) to handle recursive tree and path problems.

**3 Must-Solve:**
- [Path Sum](https://leetcode.com/problems/path-sum/)
- [Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/)
- [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

**2 Practice:**
- [Subtree of Another Tree](https://leetcode.com/problems/subtree-of-another-tree/)
- [Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)

**Classic Questions:**
- Inorder/Preorder/Postorder Traversal (recursive and iterative) [Article](https://www.geeksforgeeks.org/tree-traversals-inorder-preorder-and-postorder/) [Practice](https://practice.geeksforgeeks.org/problems/inorder-traversal/1)
- Height of a tree [Article](https://www.geeksforgeeks.org/write-a-c-program-to-find-the-maximum-depth-or-height-of-a-tree/) [Practice](https://practice.geeksforgeeks.org/problems/height-of-binary-tree/1)
- Diameter of a tree [Article](https://www.geeksforgeeks.org/diameter-of-a-binary-tree/) [Practice](https://practice.geeksforgeeks.org/problems/diameter-of-binary-tree/1)
- Boundary traversal of a Binary tree [Article](https://www.geeksforgeeks.org/boundary-traversal-of-binary-tree/) [Practice](https://practice.geeksforgeeks.org/problems/boundary-traversal-of-binary-tree/1)

---

### 9. 🥄 Two Heaps

**Explanation:**  
Maintain two heaps (min and max) to find medians in a data stream, or balance k largest/smallest elements.

**3 Must-Solve:**
- [Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/)
- [Sliding Window Median](https://leetcode.com/problems/sliding-window-median/)
- [Kth Smallest Element in a Sorted Matrix](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)

**2 Practice:**
- [Minimum Cost to Connect Sticks](https://leetcode.com/problems/minimum-cost-to-connect-sticks/)
- [Merge K Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)

**Classic Questions:**
- Maximum of all subarrays of size k [Article](https://www.geeksforgeeks.org/sliding-window-maximum-maximum-of-all-subarrays-of-size-k/) [Practice](https://practice.geeksforgeeks.org/problems/maximum-of-all-subarrays-of-size-k3101/1)
- Kth smallest and largest element in an unsorted array [Article](https://www.geeksforgeeks.org/kth-smallestlargest-element-unsorted-array/) [Practice](https://practice.geeksforgeeks.org/problems/kth-smallest-element/0)
- Merge “K” sorted arrays [Article](https://www.geeksforgeeks.org/merge-k-sorted-arrays/) [Practice](https://practice.geeksforgeeks.org/problems/merge-k-sorted-arrays/1)
- Median in a stream of Integers [Article](https://www.geeksforgeeks.org/median-of-stream-of-integers-running-integers/) [Practice](https://practice.geeksforgeeks.org/problems/find-median-in-stream-1587115620/1)

---

### 10. 🔢 Subsets & Backtracking

**Explanation:**  
Generate all combinations, permutations, or subsets by exploring all potential recursive decisions. Classic for combinatorics, permutations, and recursion.

**3 Must-Solve:**
- [Subsets](https://leetcode.com/problems/subsets/)
- [Combination Sum](https://leetcode.com/problems/combination-sum/)
- [Permutations](https://leetcode.com/problems/permutations/)

**2 Practice:**
- [N-Queens](https://leetcode.com/problems/n-queens/)
- [Word Search](https://leetcode.com/problems/word-search/)

**Classic Questions:**
- Printing all solutions in N-Queen [Article](https://www.geeksforgeeks.org/printing-solutions-n-queen-problem/) [Practice](https://practice.geeksforgeeks.org/problems/n-queen-problem0315/1)
- Subset Sum Problem [Article](https://www.geeksforgeeks.org/subset-sum-problem-dp-25/) [Practice](https://practice.geeksforgeeks.org/problems/subset-sum-problem2014/1)
- Word Break Problem using Backtracking [Article](https://www.geeksforgeeks.org/word-break-problem-using-backtracking/) [Practice](https://practice.geeksforgeeks.org/problems/word-break1352/1)
- Print all palindromic partitions of a string [Article](https://www.geeksforgeeks.org/given-a-string-print-all-possible-palindromic-partition/) [Practice](https://practice.geeksforgeeks.org/problems/palindromic-partitioning4845/1)

---

### 11. 🔍 Modified Binary Search

**Explanation:**  
Adapt binary search logic for rotated or special arrays, or to search in grids/matrices.

**3 Must-Solve:**
- [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)
- [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)
- [Peak Index in a Mountain Array](https://leetcode.com/problems/peak-index-in-a-mountain-array/)

**2 Practice:**
- [Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
- [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)

**Classic Questions:**
- Find first and last positions of an element in a sorted array [Article](https://www.geeksforgeeks.org/find-first-and-last-positions-of-an-element-in-a-sorted-array/) [Practice](https://practice.geeksforgeeks.org/problems/first-and-last-occurrence-of-x3116/1)
- Find a Fixed Point (Value equal to index) in a given array [Article](https://www.geeksforgeeks.org/find-a-fixed-point-in-a-given-array/) [Practice](https://practice.geeksforgeeks.org/problems/value-equal-to-index-value1330/1)
- Book Allocation Problem [Article](https://www.geeksforgeeks.org/allocate-minimum-number-pages/) [Practice](https://practice.geeksforgeeks.org/problems/allocate-minimum-number-of-pages0937/1)
- Aggressive cows [Article](https://www.geeksforgeeks.org/aggressive-cows-dynamic-programming-example/) [Practice](https://practice.geeksforgeeks.org/problems/aggressive-cows/1)

---

### 12. 🏆 Top K Elements (Heap-based)

**Explanation:**  
Use a heap (priority queue) to retrieve k largest/smallest elements, frequencies, or sorts.

**3 Must-Solve:**
- [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)
- [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/)
- [Kth Smallest Element in a Sorted Matrix](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)

**2 Practice:**
- [Sort Characters By Frequency](https://leetcode.com/problems/sort-characters-by-frequency/)
- [Top K Frequent Words](https://leetcode.com/problems/top-k-frequent-words/)

**Classic Questions:**
- “K” largest element in an array [Article](https://www.geeksforgeeks.org/kth-largest-element-in-an-array/) [Practice](https://practice.geeksforgeeks.org/problems/k-largest-elements3736/1)
- Kth smallest number again [Article](https://www.geeksforgeeks.org/kth-smallest-number-again/) [Practice](https://practice.geeksforgeeks.org/problems/kth-smallest-number-again/1)
- Merge “K” sorted arrays [Article](https://www.geeksforgeeks.org/merge-k-sorted-arrays/) [Practice](https://practice.geeksforgeeks.org/problems/merge-k-sorted-arrays/1)
- Smallest range in “K” Lists [Article](https://www.geeksforgeeks.org/find-smallest-range-containing-elements-from-k-lists/) [Practice](https://practice.geeksforgeeks.org/problems/find-smallest-range-containing-elements-from-k-lists/1)

---

### 13. 🧵 K-way Merge

**Explanation:**  
Efficiently merge k sorted arrays or lists, usually via a min-heap.

**3 Must-Solve:**
- [Merge K Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)
- [Smallest Range Covering Elements from K Lists](https://leetcode.com/problems/smallest-range-covering-elements-from-k-lists/)
- [Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/)

**2 Practice:**
- [Merge K Sorted Arrays](https://practice.geeksforgeeks.org/problems/merge-k-sorted-arrays/1) (GFG)
- [Kth Smallest Number in M Sorted Lists](https://www.geeksforgeeks.org/kth-smallest-element-in-row-wise-and-column-wise-sorted-2d-array/) (GFG)

**Classic Questions:**
- Merge K sorted Linked list [Article](https://www.geeksforgeeks.org/merge-k-sorted-linked-lists/) [Practice](https://practice.geeksforgeeks.org/problems/merge-k-sorted-linked-lists/1)
- Merge 2 sorted arrays without using Extra space [Article](https://www.geeksforgeeks.org/merge-two-sorted-arrays-o1-extra-space/) [Practice](https://practice.geeksforgeeks.org/problems/merge-two-sorted-arrays-1587115620/1)
- Merge 2 Binary Max Heaps [Article](https://www.geeksforgeeks.org/merge-two-binary-max-heaps/) [Practice](https://practice.geeksforgeeks.org/problems/merge-two-binary-max-heap/1)

---

### 14. 🎒 0/1 Knapsack (DP)

**Explanation:**  
Dynamic programming for optimization problems with inclusion/exclusion decisions, typically subset sum/knapsack.

**3 Must-Solve:**
- [Partition Equal Subset Sum](https://leetcode.com/problems/partition-equal-subset-sum/)
- [Target Sum](https://leetcode.com/problems/target-sum/)
- [Last Stone Weight II](https://leetcode.com/problems/last-stone-weight-ii/)

**2 Practice:**
- [Subset Sum](https://practice.geeksforgeeks.org/problems/subset-sum-problem2014/1) (GFG)
- [0/1 Knapsack](https://practice.geeksforgeeks.org/problems/0-1-knapsack-problem0945/1) (GFG)

**Classic Questions:**
- Coin Change Problem [Article](https://www.geeksforgeeks.org/coin-change-dp-7/) [Practice](https://leetcode.com/problems/coin-change/)
- Knapsack Problem [Article](https://www.geeksforgeeks.org/0-1-knapsack-problem-dp-10/) [Practice](https://practice.geeksforgeeks.org/problems/0-1-knapsack-problem0945/1)
- Binomial Coefficient Problem [Article](https://www.geeksforgeeks.org/binomial-coefficient-dp-9/) [Practice](https://practice.geeksforgeeks.org/problems/ncr1019/1)
- Maximum Profit by buying and selling a share at most twice [Article](https://www.geeksforgeeks.org/maximum-profit-by-buying-and-selling-a-share-at-most-twice/) [Practice](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/)

---

### 15. 🔁 Topological Sort (Graph + In-Degree)

**Explanation:**  
Determine task ordering in a Directed Acyclic Graph (DAG) using in-degree counting. Used for scheduling and dependency resolution.

**3 Must-Solve:**
- [Course Schedule](https://leetcode.com/problems/course-schedule/)
- [Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)
- [Alien Dictionary](https://leetcode.com/problems/alien-dictionary/) (LeetCode Premium)

**2 Practice:**
- [Parallel Courses](https://leetcode.com/problems/parallel-courses/)
- [Sequence Reconstruction](https://leetcode.com/problems/sequence-reconstruction/)

**Classic Questions:**
- Implement Topological Sort [Article](https://www.geeksforgeeks.org/topological-sorting/) [Practice](https://practice.geeksforgeeks.org/problems/topological-sort/1)
- Find whether it is possible to finish all tasks or not from given dependencies [Article](https://www.geeksforgeeks.org/find-whether-it-is-possible-to-finish-all-tasks-or-not-from-given-dependencies/) [Practice](https://practice.geeksforgeeks.org/problems/prerequisite-tasks/1)
- Minimum time taken by each job to be completed given by a Directed Acyclic Graph [Article](https://www.geeksforgeeks.org/minimum-time-taken-by-each-job-to-be-completed-given-by-a-directed-acyclic-graph/) [Practice](https://practice.geeksforgeeks.org/problems/minimum-time-taken-by-each-job-to-be-completed-given-by-a-directed-acyclic-graph/1)

---

### 16. 🔄 Floyd's Cycle Detection

**Explanation:**  
Detect cycles in linked lists or number space using the Tortoise and Hare algorithm.

**3 Must-Solve:**
- [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)
- [Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)
- [Happy Number](https://leetcode.com/problems/happy-number/)

**2 Practice:**
- [Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)
- [Detect Cycle in a Directed Graph](https://practice.geeksforgeeks.org/problems/detect-cycle-in-a-directed-graph/1) (GFG)

**Classic Questions:**
- Detect Cycle in Directed/UnDirected Graph using BFS/DFS Algo [Article](https://www.geeksforgeeks.org/detect-cycle-in-a-graph/) [Practice](https://practice.geeksforgeeks.org/problems/detect-cycle-in-an-undirected-graph/1)
- Find the starting point of the loop [Article](https://www.geeksforgeeks.org/find-first-node-of-loop-in-a-linked-list/) [Practice](https://practice.geeksforgeeks.org/problems/find-first-node-of-loop-in-linked-list/1)

---

### 17. 📈 Kadane’s Algorithm (Max Subarray Sum)

**Explanation:**  
Dynamic programming technique for finding maximum sum subarrays in O(n) time.

**3 Must-Solve:**
- [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)
- [Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)
- [Maximum Sum Circular Subarray](https://leetcode.com/problems/maximum-sum-circular-subarray/)

**2 Practice:**
- [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
- [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)

**Classic Questions:**
- Kadane's Algorithm [Article](https://www.geeksforgeeks.org/largest-sum-contiguous-subarray/) [Practice](https://practice.geeksforgeeks.org/problems/kadanes-algorithm/0)
- Find Largest sum contiguous Subarray [Article](https://www.geeksforgeeks.org/largest-sum-contiguous-subarray/) [Practice](https://practice.geeksforgeeks.org/problems/largest-sum-contiguous-subarray/1)
- LargestSum Contiguous Subarray [Article](https://www.geeksforgeeks.org/largest-sum-contiguous-subarray/) [Practice](https://practice.geeksforgeeks.org/problems/largest-sum-contiguous-subarray/1)
- Minimum sum contiguous subarray [Article](https://www.geeksforgeeks.org/smallest-sum-contiguous-subarray/) [Practice](https://practice.geeksforgeeks.org/problems/smallest-sum-contiguous-subarray/0)

---

### 18. 🧬 LCS / LCS-based (Dynamic Programming)

**Explanation:**  
Find the longest common subsequence or related variations (edit distance, subsequences) between strings via DP.

**3 Must-Solve:**
- [Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/)
- [Edit Distance](https://leetcode.com/problems/edit-distance/)
- [Longest Palindromic Subsequence](https://leetcode.com/problems/longest-palindromic-subsequence/)

**2 Practice:**
- [Distinct Subsequences](https://leetcode.com/problems/distinct-subsequences/)
- [Interleaving String](https://leetcode.com/problems/interleaving-string/)

**Classic Questions:**
- Longest Common Subsequence [Article](https://www.geeksforgeeks.org/longest-common-subsequence-dp-4/) [Practice](https://practice.geeksforgeeks.org/problems/longest-common-subsequence-1587115620/1)
- Edit Distance [Article](https://www.geeksforgeeks.org/edit-distance-dp-5/) [Practice](https://practice.geeksforgeeks.org/problems/edit-distance3702/1)
- Longest Repeated Subsequence [Article](https://www.geeksforgeeks.org/longest-repeated-subsequence/) [Practice](https://practice.geeksforgeeks.org/problems/longest-repeating-subsequence2004/1)
- Longest Palindromic Substring [Article](https://www.geeksforgeeks.org/longest-palindromic-substring-set-1/) [Practice](https://leetcode.com/problems/longest-palindromic-substring/)

---

### 19. 🔗 Union Find (Disjoint Set)

**Explanation:**  
Efficient structure for grouping elements, connected components, or cycle detection in graphs.

**3 Must-Solve:**
- [Number of Connected Components in an Undirected Graph](https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/)
- [Redundant Connection](https://leetcode.com/problems/redundant-connection/)
- [Accounts Merge](https://leetcode.com/problems/accounts-merge/)

**2 Practice:**
- [Friend Circles](https://leetcode.com/problems/friend-circles/)
- [Satisfiability of Equality Equations](https://leetcode.com/problems/satisfiability-of-equality-equations/)

**Classic Questions:**
- Check if given graph is tree or not [Article](https://www.geeksforgeeks.org/check-given-graph-tree/) [Practice](https://practice.geeksforgeeks.org/problems/is-it-a-tree/1)
- Number of Triangles in a Directed and Undirected Graph [Article](https://www.geeksforgeeks.org/number-of-triangles-in-directed-and-undirected-graphs/) [Practice](https://practice.geeksforgeeks.org/problems/number-of-triangles-in-graph/1)
- Count Strongly connected Components(Kosaraju Algo) [Article](https://www.geeksforgeeks.org/strongly-connected-components/) [Practice](https://practice.geeksforgeeks.org/problems/strongly-connected-components-kosarajus-algo/1)

---

### 20. 🔡 Trie (Prefix Tree)

**Explanation:**  
Tree-like data structure for fast prefix searching, autocomplete, and word dictionaries.

**3 Must-Solve:**
- [Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/)
- [Word Search II](https://leetcode.com/problems/word-search-ii/)
- [Search Suggestions System](https://leetcode.com/problems/search-suggestions-system/)

**2 Practice:**
- [Add and Search Word - Data structure design](https://leetcode.com/problems/add-and-search-word-data-structure-design/)
- [Replace Words](https://leetcode.com/problems/replace-words/)

**Classic Questions:**
- Construct a trie from scratch [Article](https://www.geeksforgeeks.org/trie-insert-and-search/) [Practice](https://practice.geeksforgeeks.org/problems/trie-insert-and-search/1)
- Find shortest unique prefix for every word in a given list [Article](https://www.geeksforgeeks.org/shortest-unique-prefix-for-every-word/) [Practice](https://practice.geeksforgeeks.org/problems/shortest-unique-prefix-for-every-word/1)
- Word Break Problem | (Trie solution) [Article](https://www.geeksforgeeks.org/word-break-problem-trie-solution/) [Practice](https://practice.geeksforgeeks.org/problems/word-break1352/1)
- Implement a Phone Directory [Article](https://www.geeksforgeeks.org/phone-directory-using-trie/) [Practice](https://practice.geeksforgeeks.org/problems/phone-directory4628/1)

---

## 🎯 Optional High-Impact Bonus Patterns

| Pattern                  | Use Case Example                       |
|--------------------------|----------------------------------------|
| Monotonic Stack          | Next Greater Element, Histogram Area   |
| Prefix Sum / Diff        | Range sum queries                      |
| Binary Search on Answer  | Minimize/maximize under constraint     |
| Matrix Graph BFS/DFS     | Number of Islands, Surrounded Regions  |
| Bitmasking               | Subsets, DP optimization               |

---


# 💎 Pro Mastery Tips for DSA Pattern Success / 💡 Final Tips to Master Them

Unlock your coding interview potential by focusing on smart, pattern-driven practice. Here are essential strategies to master 20 core Data Structures & Algorithms (DSA) patterns and maximize your placement/internship success.

---

## 🔁 1. Stick to the Pattern Approach

- **Don’t solve random problems**—work through problems grouped by pattern (e.g., Two Pointers, Sliding Window).
- **How:** Spend 2–3 days on one pattern at a time.
- **Why:** Enhances rapid recognition of similar problems in real interviews.

---

## 📈 2. Easy → Medium → Hard Progression

- **Approach:** For each pattern:  
  - 2 Easy  
  - 3 Medium  
  - 1 Hard
- **Benefit:** Builds confidence and deepens understanding.
- **Example (Sliding Window):**
  - *Easy:* Max Average Subarray I
  - *Medium:* Longest Substring Without Repeat
  - *Hard:* Sliding Window Maximum

---

## 🧠 3. Explain Your Code Aloud (Rubber Duck Debugging)

- **How:** Pretend you’re teaching or explaining your solution out loud.
- **Why:** Forces clarity in thought process and improves interview communication.

---

## 📒 4. Maintain a Pattern Logbook or Tracker

- **What to Track:**  
  - Pattern  
  - Problem  
  - Difficulty  
  - Time Taken  
  - Date Attempted  
  - Revisit Date  
  - Notes/Concepts (especially if you got stuck)
- **Why:** Helps visualize progress and target weak spots.

---

## 🛠️ 5. Code From Scratch Without Peeking

- **Rule:** Try solving from memory; only refer to solutions after serious effort and a break.
- **Why:** Strengthens recall under pressure.

---

## 🪛 6. Focus on Edge Cases and Constraints

- **Ask:**  
  - Can I use a map/set for optimization?
  - Is sorting + two pointers more efficient?
  - What edge cases might break my code?
- **Why:** Real interviews often test your awareness of constraints and edge-case handling.

---

## 🧮 7. Mock Interviews and Timed Solving

- **Simulate:** Use platforms with timed contests or mock interview modes.
- **Practice:** 2 problems in 60 minutes.
- **Why:** Builds real-world interview stamina and time management.

---

## 🎯 8. Do Revisions Every 7–10 Days

- **Spaced Repetition:**  
  - Day 1: Solve  
  - Day 3: Recall & re-solve  
  - Day 7: Review again
- **Why:** Solidifies patterns in long-term memory, especially for recursion/DP.

---

## ⏳ 9. Don’t Over-Solve — Understand Instead

- **Goal:** 3–5 problems per pattern with deep understanding beats 50 shallow solves.
- **Why:** Quality and comprehension matter more than sheer quantity.

---

## 👨‍💻 10. Apply to Real Problems

- **Where:**  
  - InterviewBit (pattern-based levels)  
  - CodeStudio (Coding Ninjas)  
  - GeeksforGeeks Must Do 190  
  - Striver’s SDE Sheet
- **Why:** Practice with real-world, interview-tested problems.

---

# 🏁 Summary

- 🔍 Focus on **patterns**, not just topics.
- 🎯 Practice **smart and deep**, not just hard.
- 🧠 **Understand** before you memorize.
- ⏱️ **Stay consistent**, track progress, and revisit frequently for mastery.

---
