# 🎯 Week 23: Linked Lists, Stacks & Queues

> **Duration:** 24 hours | **Difficulty:** 🟡 Intermediate | **Prerequisites:** Week 21-22

## 📌 Goal

Master linked list operations and pointer manipulation. Learn stack and queue data structures and their applications in real-world problems.

## 🎓 Learning Objectives

By the end of this week, you will:
- ✅ Understand linked list structure and operations
- ✅ Implement single and doubly linked lists
- ✅ Solve complex linked list problems
- ✅ Master stack and queue implementations
- ✅ Understand circular queues and deques
- ✅ Learn monotonic stack pattern
- ✅ Apply to real-world problems

## 📚 Prerequisites
- Big O complexity analysis (Week 21)
- Pointer concepts
- Basic recursion

## 📖 Concepts

### Linked List Fundamentals

#### Node Structure

```javascript
class Node {
    constructor(val) {
        this.val = val;
        this.next = null;
    }
}

class LinkedList {
    constructor() {
        this.head = null;
        this.tail = null;
        this.size = 0;
    }
}
```

#### Singly Linked List Operations

```javascript
class SinglyLinkedList {
    constructor() {
        this.head = null;
        this.size = 0;
    }
    
    // Insert at beginning: O(1)
    insertFirst(val) {
        const node = new Node(val);
        node.next = this.head;
        this.head = node;
        this.size++;
    }
    
    // Insert at end: O(n)
    insertLast(val) {
        const node = new Node(val);
        if (!this.head) {
            this.head = node;
        } else {
            let current = this.head;
            while (current.next) {
                current = current.next;
            }
            current.next = node;
        }
        this.size++;
    }
    
    // Search: O(n)
    search(target) {
        let current = this.head;
        while (current) {
            if (current.val === target) return true;
            current = current.next;
        }
        return false;
    }
    
    // Delete: O(n)
    delete(val) {
        if (!this.head) return;
        
        // If head matches
        if (this.head.val === val) {
            this.head = this.head.next;
            this.size--;
            return;
        }
        
        let current = this.head;
        while (current.next) {
            if (current.next.val === val) {
                current.next = current.next.next;
                this.size--;
                return;
            }
            current = current.next;
        }
    }
}
```

#### Linked List vs Array

| Operation | Array | Linked List |
|-----------|-------|-------------|
| Access | O(1) | O(n) |
| Insert first | O(n) | O(1) |
| Insert last | O(1) | O(n) |
| Delete | O(n) | O(n) |
| Search | O(n) | O(n) |
| Space | Fixed | Dynamic |

### Complex Linked List Problems

#### Example 1: Reverse Linked List

```javascript
function reverseList(head) {
    let prev = null;
    let current = head;
    
    while (current) {
        // Store next node
        const next = current.next;
        
        // Reverse the link
        current.next = prev;
        
        // Move pointers forward
        prev = current;
        current = next;
    }
    
    return prev; // New head
}

// Example: 1 → 2 → 3 → null
// Result:  null ← 1 ← 2 ← 3
// Time: O(n), Space: O(1)
```

#### Example 2: Detect Cycle (Floyd's Algorithm)

```javascript
function detectCycle(head) {
    let slow = head;
    let fast = head;
    
    // Phase 1: Detect cycle
    while (fast && fast.next) {
        slow = slow.next;
        fast = fast.next.next;
        
        if (slow === fast) {
            // Cycle detected
            // Phase 2: Find cycle start
            let ptr1 = head;
            let ptr2 = slow;
            
            while (ptr1 !== ptr2) {
                ptr1 = ptr1.next;
                ptr2 = ptr2.next;
            }
            
            return ptr1; // Cycle start
        }
    }
    
    return null; // No cycle
}

// Time: O(n), Space: O(1)
```

#### Example 3: Merge Two Sorted Lists

```javascript
function mergeTwoLists(l1, l2) {
    const dummy = new Node(0);
    let current = dummy;
    
    while (l1 && l2) {
        if (l1.val <= l2.val) {
            current.next = l1;
            l1 = l1.next;
        } else {
            current.next = l2;
            l2 = l2.next;
        }
        current = current.next;
    }
    
    // Attach remaining
    current.next = l1 || l2;
    
    return dummy.next;
}

// Time: O(n + m), Space: O(1)
```

### Stack Data Structure

#### Stack Implementation

```javascript
class Stack {
    constructor() {
        this.items = [];
    }
    
    // Push: O(1)
    push(val) {
        this.items.push(val);
    }
    
    // Pop: O(1)
    pop() {
        return this.items.pop();
    }
    
    // Peek: O(1)
    peek() {
        return this.items[this.items.length - 1];
    }
    
    // Is empty: O(1)
    isEmpty() {
        return this.items.length === 0;
    }
    
    // Size: O(1)
    size() {
        return this.items.length;
    }
}
```

#### Stack Applications

**Example: Balanced Parentheses**

```javascript
function isBalanced(s) {
    const stack = new Stack();
    const pairs = { ')': '(', '}': '{', ']': '[' };
    
    for (let char of s) {
        if (['(', '{', '['].includes(char)) {
            stack.push(char);
        } else if ([')', '}', ']'].includes(char)) {
            if (stack.isEmpty() || stack.pop() !== pairs[char]) {
                return false;
            }
        }
    }
    
    return stack.isEmpty();
}

// Time: O(n), Space: O(n)
```

### Queue Data Structure

#### Queue Implementation

```javascript
class Queue {
    constructor() {
        this.items = {};
        this.count = 0;
        this.head = 0;
    }
    
    // Enqueue: O(1)
    enqueue(val) {
        this.items[this.count] = val;
        this.count++;
    }
    
    // Dequeue: O(1)
    dequeue() {
        if (this.isEmpty()) return undefined;
        
        const result = this.items[this.head];
        delete this.items[this.head];
        this.head++;
        return result;
    }
    
    // Peek: O(1)
    peek() {
        return this.items[this.head];
    }
    
    // Is empty: O(1)
    isEmpty() {
        return this.count - this.head === 0;
    }
    
    // Size: O(1)
    size() {
        return this.count - this.head;
    }
}
```

#### Circular Queue

```javascript
class CircularQueue {
    constructor(k) {
        this.queue = new Array(k);
        this.head = -1;
        this.tail = -1;
        this.size = k;
    }
    
    enqueue(val) {
        if (this.isFull()) return false;
        
        if (this.head === -1) {
            this.head = 0;
        }
        
        this.tail = (this.tail + 1) % this.size;
        this.queue[this.tail] = val;
        return true;
    }
    
    dequeue() {
        if (this.isEmpty()) return false;
        
        if (this.head === this.tail) {
            this.head = -1;
            this.tail = -1;
            return true;
        }
        
        this.head = (this.head + 1) % this.size;
        return true;
    }
    
    isFull() {
        return (this.tail + 1) % this.size === this.head;
    }
    
    isEmpty() {
        return this.head === -1;
    }
}
```

### Deque (Double-Ended Queue)

```javascript
class Deque {
    constructor() {
        this.items = {};
        this.count = 0;
        this.head = 0;
    }
    
    // Add to front: O(1)
    addFront(val) {
        if (this.head > 0) {
            this.head--;
            this.items[this.head] = val;
        } else {
            this.items[this.count] = this.items[this.head];
            this.items[this.head] = val;
            this.count++;
        }
    }
    
    // Add to rear: O(1)
    addRear(val) {
        this.items[this.count] = val;
        this.count++;
    }
    
    // Remove front: O(1)
    removeFront() {
        if (this.isEmpty()) return undefined;
        const result = this.items[this.head];
        delete this.items[this.head];
        this.head++;
        return result;
    }
    
    // Remove rear: O(1)
    removeRear() {
        if (this.isEmpty()) return undefined;
        this.count--;
        const result = this.items[this.count];
        delete this.items[this.count];
        return result;
    }
}
```

### Monotonic Stack

Stack maintaining elements in sorted order.

**Example: Next Greater Element**

```javascript
function nextGreaterElement(nums) {
    const result = new Array(nums.length).fill(-1);
    const stack = [];
    
    for (let i = nums.length - 1; i >= 0; i--) {
        // Pop smaller elements
        while (stack.length > 0 && stack[stack.length - 1] <= nums[i]) {
            stack.pop();
        }
        
        // Top of stack is next greater
        if (stack.length > 0) {
            result[i] = stack[stack.length - 1];
        }
        
        // Add current element
        stack.push(nums[i]);
    }
    
    return result;
}

// Example: [1, 2, 1]
// Result: [2, -1, 2]
// Time: O(n), Space: O(n)
```

## 📅 Daily Study Plan

### Monday & Tuesday: Linked Lists (8 hours)

**Monday:**
- Hours 1-2: Linked list basics and operations
- Hours 2-3: Implement single linked list
- Hours 3-4: Solve 5 basic linked list problems

**Tuesday:**
- Hours 1-2: Complex linked list problems
- Hours 2-3: Cycle detection, merging, reversing
- Hours 3-4: Solve 5 advanced linked list problems

### Wednesday: Stacks (4 hours)

- Hour 1: Stack fundamentals and implementation
- Hours 2-3: Stack applications
- Hours 3-4: Solve 5 stack problems

### Thursday: Queues & Deques (4 hours)

- Hour 1: Queue fundamentals
- Hours 2-3: Circular queues and deques
- Hours 3-4: Solve 5 queue problems

### Friday: Problem Solving & Projects
**Duration:** 3 hours

- Hour 1: Mixed problems with all data structures
- Hours 2-3: Start mini projects

### Saturday & Sunday: Mini Projects
**Duration:** 3 hours each

- Build three mini projects

## 📋 Practice Problems

### Linked Lists (Easy-Medium)

1. **Reverse Linked List** - [LeetCode 206](https://leetcode.com/problems/reverse-linked-list/)
2. **Linked List Cycle** - [LeetCode 141](https://leetcode.com/problems/linked-list-cycle/)
3. **Merge Two Sorted Lists** - [LeetCode 21](https://leetcode.com/problems/merge-two-sorted-lists/)
4. **Middle of Linked List** - [LeetCode 876](https://leetcode.com/problems/middle-of-the-linked-list/)
5. **Remove Nth Node** - [LeetCode 19](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

### Stacks (Easy-Medium)

1. **Valid Parentheses** - [LeetCode 20](https://leetcode.com/problems/valid-parentheses/)
2. **Min Stack** - [LeetCode 155](https://leetcode.com/problems/min-stack/)
3. **Next Greater Element** - [LeetCode 496](https://leetcode.com/problems/next-greater-element-i/)
4. **Daily Temperatures** - [LeetCode 739](https://leetcode.com/problems/daily-temperatures/)
5. **Evaluate Reverse Polish Notation** - [LeetCode 150](https://leetcode.com/problems/evaluate-reverse-polish-notation/)

### Queues (Easy-Medium)

1. **Number of Recent Calls** - [LeetCode 933](https://leetcode.com/problems/number-of-recent-calls/)
2. **Reveal Cards in Increasing Order** - [LeetCode 950](https://leetcode.com/problems/reveal-cards-in-increasing-order/)
3. **Moving Average from Data Stream** - [LeetCode 346](https://leetcode.com/problems/moving-average-from-data-stream/)

## 💻 Mini Projects

### Project 1: Undo/Redo System
**Duration:** 4 hours | **Difficulty:** 🟡 Intermediate

#### Features
1. Stack-based undo/redo
2. Text editor with operations
3. Visual history
4. Keyboard shortcuts

#### Skills
- Stack implementation
- Command pattern
- UI/UX

### Project 2: Browser History
**Duration:** 4 hours | **Difficulty:** 🟡 Intermediate

#### Features
1. Forward/backward navigation
2. History visualization
3. Duplicate URL handling
4. Clear history

#### Tech Stack
- React or Vue
- Stack data structure

### Project 3: Music Queue Player
**Duration:** 3 hours | **Difficulty:** 🟡 Intermediate

#### Features
1. Queue-based playlist
2. Shuffle functionality
3. Repeat modes
4. Seek operations

## ✅ Revision Checklist

- [ ] Implement single linked list from scratch
- [ ] Solve linked list cycle detection
- [ ] Implement stack and queue
- [ ] Solve stack problems (parentheses, monotonic)
- [ ] Solve queue problems
- [ ] Completed 3 mini projects
- [ ] Solved 15+ practice problems
- [ ] Ready for Week 24

---

**Next:** [Week 24 - Hash Maps & Heaps →](Week-24.md)
