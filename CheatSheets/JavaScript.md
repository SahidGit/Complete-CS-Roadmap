# JavaScript Cheat Sheet

Core ECMAScript syntax, DOM manipulation, and asynchronous programming.

## Modern JS Reference

### 1. Variables and Scope
Use `const` by default. Only use `let` if you need to reassign a value. Avoid `var` entirely:
```javascript
const name = "Sahid"; // Block-scoped, immutable binding
let count = 0; // Block-scoped, mutable value
```

### 2. Useful Array Methods
```javascript
const items = [{ id: 1, value: 10 }, { id: 2, value: 20 }];

// Map: Transform values
const values = items.map(item => item.value); // [10, 20]

// Filter: Extract elements matching a condition
const highValues = items.filter(item => item.value > 15); // [{ id: 2, value: 20 }]

// Reduce: Aggregate values
const total = items.reduce((acc, item) => acc + item.value, 0); // 30
```

### 3. Asynchronous Programming (Async/Await)
```javascript
async function fetchUsers() {
  try {
    const response = await fetch("https://api.github.com/users/SahidGit");
    if (!response.ok) throw new Error(`HTTP error! Status: ${response.status}`);
    const data = await response.json();
    return data;
  } catch (error) {
    console.error("Failed to fetch user:", error);
  }
}
```

---

## ⚠️ Common Pitfalls & Anti-Patterns

> [!WARNING]
> Side effects, memory leaks, and wrong scoping models will cause bugs in application state.

### 1. Equality Operators
Always use strict equality (`===`) instead of loose equality (`==`):
```javascript
// BAD: Performs type coercion which leads to unexpected truths
"" == 0; // true
[] == false; // true

// GOOD: Strictly checks both type and value
"" === 0; // false
```

### 2. Event Listener Memory Leaks
If you dynamically attach event listeners, make sure to clean them up when they are no longer needed:
```javascript
const controller = new AbortController();

window.addEventListener('resize', handleResize, { signal: controller.signal });

// To clean up/remove listener:
controller.abort();
```

---

## Authoritative Documentation
- [MDN Web Docs: JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [JavaScript.info: The Modern JavaScript Tutorial](https://javascript.info/)
