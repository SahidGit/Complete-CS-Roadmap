# 🎯 Week 28: Greedy, Backtracking & Divide and Conquer

> **Duration:** 24 hours | **Difficulty:** 🟡 Intermediate | **Prerequisites:** Weeks 21, 23 & 25

## 📌 Goal
Master problem-solving paradigms: locally optimal choices (Greedy), deep search space pruning (Backtracking), and subproblem partition/merges (Divide & Conquer).

---

## 🎓 Learning Objectives
By the end of this week, you will:
- ✅ Formulate Greedy proofs and understand greedy choice structures
- ✅ Implement systematic Backtracking algorithms for permutations and combinations
- ✅ Apply pruning rules to speed up backtracking recursion
- ✅ Design Divide & Conquer splits (such as QuickSelect or Merge operations)
- ✅ Code automated solvers for puzzles (Sudoku, N-Queens, Maze navigation)

---

## 📚 Prerequisites & Study Hours
- **Prerequisites**: Week 21 (Recursion), Week 23 (Stacks), Week 25 (Decision Trees)
- **Estimated Study Hours**: 24 hours
- **Difficulty**: 🟡 Intermediate

---

## 📖 Concepts & Theory

### 1. Greedy Choice Paradigm
An algorithm that makes the locally optimal choice at each stage with the hope of finding a global optimum.
- Unlike DP, Greedy does not re-evaluate previous decisions.
- *Proof of Correctness*: Requires proving greedy choice property (a local optimum belongs to a global optimum) and optimal substructure.
- *Examples*: Activity Selection, Minimum Coin Change (for standard denominations).

### 2. Backtracking (State Space Search)
An algorithmic paradigm that tries to construct a solution incrementally, one piece at a time, removing those candidates that fail to satisfy the constraints.

```
                  (Root State)
                 /     |      \
            [Choice 1] [...]  [Choice N]
              /                \
         [Pruned] (Invalid)   [Valid State] ──► Goal Found!
```

### 3. Divide & Conquer
1. **Divide**: Split the problem into smaller subproblems.
2. **Conquer**: Solve the subproblems recursively.
3. **Combine**: Merge the subproblem results to solve the original query.
- *Formula (Master Theorem)*: Used to determine time complexities of divide-and-conquer recurrences:
  $$T(n) = aT(n/b) + f(n)$$

---

## 💻 Daily Study Plan

### 📅 Monday: Greedy Algorithm Foundations
- Study Activity Selection and Fractional Knapsack algorithms.
- Complete proofs for scheduling problems.

### 📅 Tuesday: Basic Backtracking Templates
- Write backtracking templates to generate **Subsets** and **Permutations** of a list.
- Learn standard variable pruning constraints.

### 📅 Wednesday: Constraint Satisfaction Puzzles
- Solve the **N-Queens** puzzle on paper, then write the code.
- Implement constraint tracking (using row, column, and diagonal sets).

### 📅 Thursday: Divide & Conquer Implementations
- Learn QuickSelect ($O(N)$ average selection algorithm) and binary exponentiation ($O(\log N)$).
- Walk through Master Theorem evaluations.

### 📅 Friday: Projects Implementation
- Code the **Sudoku Solver** and **Maze Path Solver** projects.

### 📅 Saturday: Problem Practice
- Solve the 30 practice problems on LeetCode/Codeforces.

### 📅 Sunday: Revision & Interview Prep
- Walk through time complexities of recursion systems and backtracking trees.

---

## ⚠️ Best Practices & Common Mistakes

### Best Practices
- **Backtrack State Cleanups**: Always undo the state change after a recursive call returns (e.g. `path.push(val); backtrack(); path.pop()`).
- **Prune Early**: Add boundary/validity checks *before* making the recursive call to prevent traversing dead branches.

### Common Mistakes
- **Unbounded Recursion Trees**: Forgetting termination/base cases causes stack overflows.
- **Copying Arrays in Recursion**: Creating array copies (`arr.slice()`) on every recursive step degrades performance. Pass array index references instead.

---

## 🧪 Projects & Implementation Guide

### Project 1: Visual Sudoku Solver
- **Architecture**: A backtracking solver using Constraint Propagation to solve Sudoku boards.
- **Folder Structure**:
  ```
  sudoku-solver/
  ├── Solver.js
  ├── boards.json
  └── index.html
  ```
- **Implementation Guide**: Check if a number is valid in a $3\times3$ subgrid, row, and column. Recurse.

### Project 2: N-Queens Solution Visualizer
- **Architecture**: App generating all valid placements for $N$ queens on an $N \times N$ chessboard.

### Project 3: Automated Maze Path Finder
- **Architecture**: Backtracking bot navigating a grid map, finding paths while bypassing blocks.

---

## 📝 Practice Problems (30 Questions)

### Easy (10 Problems)
1. LeetCode 455: Assign Cookies
2. LeetCode 1221: Split a String in Balanced Strings
3. LeetCode 78: Subsets
4. LeetCode 169: Majority Element
5. GeeksforGeeks: Fractional Knapsack
6. HackerRank: Grid Challenge
7. InterviewBit: Meeting Rooms
8. AtCoder abc076_b: Addition and Multiplication
9. Codeforces 996A: Hit the Lottery
10. CodeChef: Largest Rectangle

### Medium (10 Problems)
11. LeetCode 46: Permutations
12. LeetCode 39: Combination Sum
13. LeetCode 55: Jump Game
14. LeetCode 22: Generate Parentheses
15. LeetCode 53: Maximum Subarray
16. GeeksforGeeks: N-Queens Problem
17. InterviewBit: Permutations
18. Codeforces 1526C2: Potions
19. AtCoder abc122_c: GeT AC
20. CodeChef: Weapon Value

### Hard (10 Problems)
21. LeetCode 51: N-Queens
22. LeetCode 37: Sudoku Solver
23. LeetCode 135: Candy
24. LeetCode 79: Word Search
25. LeetCode 403: Frog Jump
26. GeeksforGeeks: Solve the Sudoku
27. InterviewBit: Sudoku
28. Codeforces 1601C: Optimal Insertion
29. AtCoder abc130_f: Minimum Bounding Box
30. CodeChef: Bear and House Queries

---

## 💼 Interview Questions & Answers
- **Q**: What is the difference between backtracking and brute force?
- **A**: Brute force generates all possible candidates and checks each one for validity. Backtracking generates candidates incrementally and discards (prunes) a candidate path as soon as it determines it cannot possibly lead to a valid solution, avoiding checking the rest of that branch.

---

## 📖 Official Resources
- [Master Theorem Guide (CLRS Reference)](https://mitpress.mit.edu/9780262046304/introduction-to-algorithms/)
- [GeeksforGeeks Backtracking Tutorials](https://www.geeksforgeeks.org/backtracking-algorithms/)
