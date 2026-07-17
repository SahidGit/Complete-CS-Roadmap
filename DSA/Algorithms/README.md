# 🏃‍♂️ Algorithms Reference

This section catalogs standard algorithm design paradigms, traversal methods, and optimal system architectures.

---

## 📚 Key Paradigm Directories

### 1. Sorting & Searching
- **Bubble, Selection, Insertion**: Basic quadratic $O(n^2)$ comparison sorting.
- **Merge, Quick, Heap Sort**: Linearithmic $O(n \log n)$ divide-and-conquer/heap sorting.
- **Binary Search**: Logarithmic $O(\log n)$ search on ordered arrays and search-space boundaries.

### 2. Greedy Algorithms
- Local optimization that aims to find a global optimum.
- *Examples:* Huffman Coding, Kruskal's/Prim's MST, Dijkstra's Shortest Path, Fractional Knapsack.

### 3. Backtracking
- Depth-first systematic state exploration, discarding paths that fail constraints (pruning).
- *Examples:* N-Queens, Sudoku Solver, Subset Generation, Permutations.

### 4. Dynamic Programming (DP)
- Solves problems with **Overlapping Subproblems** and **Optimal Substructure** by caching intermediate evaluations.
- **Memoization (Top-Down)**: Recursive caching of subproblem states.
- **Tabulation (Bottom-Up)**: Iterative computation filling a DP array/matrix.
- *Classic Problems:* 0/1 Knapsack, Longest Common Subsequence (LCS), Longest Increasing Subsequence (LIS), Edit Distance.

### 5. Advanced Algorithms
- **String Matching**: Knuth-Morris-Pratt (KMP), Rabin-Karp (Rolling Hash).
- **Range Queries**: Segment Trees, Fenwick Trees (Binary Indexed Trees), Sparse Tables.

---

## 🔗 Learning Links
- [Algorithms Cheatsheet](../CheatSheets/README.md)
- [Practice Problems on LeetCode](../LeetCode/README.md)
