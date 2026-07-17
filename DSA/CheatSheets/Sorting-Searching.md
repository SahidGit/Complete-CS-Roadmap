# 🔄 Sorting & Searching Algorithms Reference Sheet

A quick-reference guide for sorting and searching algorithm complexities.

---

## ⚡ Sorting Algorithms Complexity

| Algorithm | Best Time | Average Time | Worst Time | Space | Stable? | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Bubble Sort** | $O(n)$ | $O(n^2)$ | $O(n^2)$ | $O(1)$ | Yes | Simple comparison. $O(n)$ if already sorted. |
| **Selection Sort**| $O(n^2)$ | $O(n^2)$ | $O(n^2)$ | $O(1)$ | No | Always takes $O(n^2)$ comparisons. |
| **Insertion Sort**| $O(n)$ | $O(n^2)$ | $O(n^2)$ | $O(1)$ | Yes | Excellent for small or mostly sorted arrays. |
| **Merge Sort** | $O(n \log n)$| $O(n \log n)$| $O(n \log n)$| $O(n)$ | Yes | Stable, but requires extra space. |
| **Quick Sort** | $O(n \log n)$| $O(n \log n)$| $O(n^2)$ | $O(\log n)$ | No | In-place. Worst case happens with bad pivot choice. |
| **Heap Sort** | $O(n \log n)$| $O(n \log n)$| $O(n \log n)$| $O(1)$ | No | In-place, guaranteed $O(n \log n)$. |

---

## 🔍 Searching Algorithms Complexity

| Algorithm | Best Time | Average Time | Worst Time | Space | Prerequisites |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Linear Search** | $O(1)$ | $O(n)$ | $O(n)$ | $O(1)$ | None |
| **Binary Search** | $O(1)$ | $O(\log n)$ | $O(\log n)$ | $O(1)$ | Array must be sorted |
