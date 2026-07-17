# 🎯 Week 25: Trees, BST, AVL & Trie Structures

> **Duration:** 24 hours | **Difficulty:** 🔴 Advanced | **Prerequisites:** Week 24

## 📌 Goal
Understand hierarchical data layout systems, master Binary Search Trees, balance nodes with AVL trees, and optimize word prefix storage using Tries.

---

## 🎓 Learning Objectives
By the end of this week, you will:
- ✅ Implement Binary Trees and Binary Search Trees (BST) from scratch
- ✅ Master Tree Traversals: In-order, Pre-order, Post-order, and Level-order (BFS)
- ✅ Understand self-balancing tree logic (AVL tree left/right rotations)
- ✅ Build a Trie (Prefix Tree) for auto-complete storage
- ✅ Analyze complexities of tree-based query structures

---

## 📚 Prerequisites & Study Hours
- **Prerequisites**: Week 21 (Complexity Analysis), Week 23 (Recursion & Queue buffers), Week 24 (Heaps)
- **Estimated Study Hours**: 24 hours
- **Difficulty**: 🔴 Advanced

---

## 📖 Concepts & Theory

### 1. Binary Tree Traversals
Trees are non-linear, hierarchical collections.
- **In-Order (Left, Root, Right)**: Prints BSTs in sorted ascending order.
- **Pre-Order (Root, Left, Right)**: Used to clone trees.
- **Post-Order (Left, Right, Root)**: Used in directory space checks (bottom-up calculations).
- **Level-Order (BFS)**: Traverses layer by layer using a Queue buffer.

```
       [ 1 ]
      /     \
   [ 2 ]   [ 3 ]
   /   \
 [ 4 ] [ 5 ]

In-Order:   4 -> 2 -> 5 -> 1 -> 3
Pre-Order:  1 -> 2 -> 4 -> 5 -> 3
Post-Order: 4 -> 5 -> 2 -> 3 -> 1
```

### 2. Balanced Trees (AVL Trees)
An **AVL Tree** is a self-balancing BST where the height difference between left and right subtrees (Balance Factor) of any node is at most 1.
- If $|Balance\ Factor| > 1$, perform left/right rotations to restore balance.

```
   (Unbalanced)          (Right Rotation)         (Balanced)
       [ 3 ]                                        [ 2 ]
      /                                            /     \
   [ 2 ]                 ───────────────►        [ 1 ]  [ 3 ]
  /
[ 1 ]
```

### 3. Trie (Prefix Tree)
A search tree used to search for keys in a dataset of strings. Each node represents a single character.

```
       (root)
       /    \
     [a]    [c]
     /        \
   [n]        [a]
   /            \
 [t]*           [t]*   (* denotes word endpoints)
```

---

## 💻 Daily Study Plan

### 📅 Monday: Binary Tree Foundations
- Implement a `TreeNode` class (holding value, left, and right pointers).
- Write recursive functions for In-order, Pre-order, and Post-order traversals.

### 📅 Tuesday: Binary Search Trees (BST)
- Study insertion, deletion, and retrieval methods in a BST.
- Learn $O(\log n)$ average vs $O(n)$ worst-case skew complexities.

### 📅 Wednesday: Self-Balancing Trees (AVL)
- Study rotation logic: LL (Left-Left), RR, LR, and RL cases.
- Walk through a manual AVL balancing example on paper.

### 📅 Thursday: Tries (Prefix Trees)
- Implement a `TrieNode` with a children array or hash map, and an `isEndOfWord` boolean.
- Write `insert()`, `search()`, and `startsWith()` methods.

### 📅 Friday: Projects Implementation
- Build the **Autocomplete Engine** and **Hierarchy Viewer** projects.

### 📅 Saturday: Problem Practice
- Solve the 30 tree practice problems on LeetCode/Codeforces.

### 📅 Sunday: Revision & Interview Prep
- Review tree complexities and practice whiteboard tree questions.

---

## ⚠️ Best Practices & Common Mistakes

### Best Practices
- **Handle Null Pointers**: Always write base checks `if (node === null) return` to prevent segfaults or null pointer reference calls.
- **Utilize BST Properties**: When searching in a BST, do not visit both subtrees. Go left if target < parent, else go right.

### Common Mistakes
- **Forgetting to Update AVL Heights**: Rotations must recalculate node heights to keep balancing checks accurate.
- **Forgetting Trie End-of-Word Flags**: Forgetting to set `isEndOfWord = true` makes prefix searches identify intermediate segments as complete words.

---

## 🧪 Projects & Implementation Guide

### Project 1: Autocomplete Engine
- **Architecture**: A Trie structure storing a large dictionary of words. Substring inputs return all words sharing the prefix.
- **Folder Structure**:
  ```
  autocomplete/
  ├── Trie.js
  ├── dictionary.json
  └── server.js
  ```
- **Implementation Guide**: Traverse down the prefix path, then perform a DFS from the prefix endpoint to gather matching completions.

### Project 2: Dictionary Search API
- **Architecture**: Fast spelling autocorrect interface using a Trie with Edit Distance checks.

### Project 3: Organization Hierarchy Viewer
- **Architecture**: N-ary tree parsing employee relations, outputting HTML/SVG charts.

---

## 📝 Practice Problems (30 Questions)

### Easy (10 Problems)
1. LeetCode 104: Maximum Depth of Binary Tree
2. LeetCode 100: Same Tree
3. LeetCode 226: Invert Binary Tree
4. LeetCode 112: Path Sum
5. LeetCode 700: Search in a Binary Search Tree
6. GeeksforGeeks: Size of Binary Tree
7. HackerRank: Tree: Height of a Binary Tree
8. InterviewBit: Path to Given Node
9. AtCoder abc126_d: Even Relation
10. CodeChef: Tree Balancer

### Medium (10 Problems)
11. LeetCode 102: Binary Tree Level Order Traversal
12. LeetCode 230: Kth Smallest Element in a BST
13. LeetCode 208: Implement Trie (Prefix Tree)
14. LeetCode 98: Validate Binary Search Tree
15. LeetCode 236: Lowest Common Ancestor of a Binary Tree
16. GeeksforGeeks: Check if Tree is Balanced
17. InterviewBit: Root to Leaf Paths With Sum
18. Codeforces 115A: Party
19. AtCoder abc070_d: Transit Tree Path
20. CodeChef: Rooted Tree Queries

### Hard (10 Problems)
21. LeetCode 124: Binary Tree Maximum Path Sum
22. LeetCode 297: Serialize and Deserialize Binary Tree
23. LeetCode 212: Word Search II
24. LeetCode 1382: Balance a Binary Search Tree
25. LeetCode 99: Recover Binary Search Tree
26. GeeksforGeeks: Max path sum between two leaf nodes
27. InterviewBit: Binary Tree Postorder Traversal
28. Codeforces 274B: Zero Tree
29. AtCoder abc133_f: Colorful Tree
30. CodeChef: Querying on Tree

---

## 💼 Interview Questions & Answers
- **Q**: What is the difference between BFS and DFS on trees?
- **A**: BFS (Breadth-First Search) visits nodes level by level using a Queue, requiring $O(W)$ memory where $W$ is the maximum width of the tree. DFS (Depth-First Search) goes deep into subtrees using recursion (System Stack), requiring $O(H)$ memory where $H$ is the tree height.

---

## 📖 Official Resources
- [C++ std::map (Red-Black Tree implementation)](https://en.cppreference.com/w/cpp/container/map)
- [Java TreeMap Class Documentation](https://docs.oracle.com/javase/8/docs/api/java/util/TreeMap.html)
