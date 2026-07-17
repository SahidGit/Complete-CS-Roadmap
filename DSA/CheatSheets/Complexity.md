# 📊 Big O Complexity Reference Sheet

A quick-reference guide for standard time and space complexities of data structure operations.

---

## 🏗️ Data Structure Operations Complexity

| Data Structure | Access | Search | Insertion | Deletion | Space Complexity |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Array** | $O(1)$ | $O(n)$ | $O(n)$ | $O(n)$ | $O(n)$ |
| **Stack** | $O(n)$ | $O(n)$ | $O(1)$ | $O(1)$ | $O(n)$ |
| **Queue** | $O(n)$ | $O(n)$ | $O(1)$ | $O(1)$ | $O(n)$ |
| **Singly Linked List** | $O(n)$ | $O(n)$ | $O(1)$ | $O(1)$ | $O(n)$ |
| **Doubly Linked List** | $O(n)$ | $O(n)$ | $O(1)$ | $O(1)$ | $O(n)$ |
| **Hash Table** | $N/A$ | $O(1)$ | $O(1)$ | $O(1)$ | $O(n)$ |
| **Binary Search Tree** | $O(\log n)$ | $O(\log n)$ | $O(\log n)$ | $O(\log n)$ | $O(n)$ |
| **AVL Tree** | $O(\log n)$ | $O(\log n)$ | $O(\log n)$ | $O(\log n)$ | $O(n)$ |
| **Red-Black Tree** | $O(\log n)$ | $O(\log n)$ | $O(\log n)$ | $O(\log n)$ | $O(n)$ |

*Note: Tree complexities are average/worst cases on balanced configurations. Skewed trees degrade to $O(n)$.*

---

## 📈 Big O Curves

- **$O(1)$**: Constant. Size doesn't affect execution time (e.g. array index lookup).
- **$O(\log n)$**: Logarithmic. Divides search space in half (e.g. binary search).
- **$O(n)$**: Linear. Iterates through the entire dataset once (e.g. finding minimum value).
- **$O(n \log n)$**: Linearithmic. Splits dataset and sorts subsets (e.g. mergesort).
- **$O(n^2)$**: Quadratic. Nested iteration (e.g. bubble sort).
- **$O(2^n)$**: Exponential. Doubling execution paths (e.g. recursive Fibonacci).
- **$O(n!)$**: Factorial. Permuting all elements (e.g. traveling salesperson brute force).
