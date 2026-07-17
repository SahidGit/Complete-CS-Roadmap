# 🗄️ Data Structures Reference

Data structures are specific methods of organizing and storing data in a computer so that they can be accessed and modified efficiently.

---

## 🏗️ Core Structures Catalog

### 1. Linear Structures
- **Arrays & Strings**: Contiguous blocks of memory. Support $O(1)$ index access.
- **Linked Lists**: Node chains containing values and pointers. Support $O(1)$ insertions at boundaries.
- **Stacks**: Last-In-First-Out (LIFO) structures (push/pop).
- **Queues & Deques**: First-In-First-Out (FIFO) and Double-Ended Queue configurations.

### 2. Hash-Based Structures
- **Hash Maps & Hash Sets**: Key-value pairs indexed by hashes. Support average $O(1)$ lookups, inserts, and deletes.

### 3. Tree-Based Structures
- **Binary Trees**: Hierarchical structures where nodes have at most two children.
- **Binary Search Trees (BST)**: Binary trees where left subtree values < parent node < right subtree values.
- **Self-Balancing Trees**: AVL Trees and Red-Black Trees that maintain balanced heights to ensure $O(\log n)$ queries.
- **Heaps / Priority Queues**: Complete binary trees that maintain heap-order property (Min/Max values at root in $O(1)$ time).
- **Tries (Prefix Trees)**: Specialized search trees used for efficient string/key lookups.

### 4. Graph-Based Structures
- Collections of **Nodes (Vertices)** connected by **Edges**.
- Represented as **Adjacency Matrices** or **Adjacency Lists**.
- Traversed using **Depth-First Search (DFS)** or **Breadth-First Search (BFS)**.

---

## 🔗 Learning Links
- [Data Structures Cheatsheet](../CheatSheets/README.md)
- [Weekly Implementations](../../weeks/)
