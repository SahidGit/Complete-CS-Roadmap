# React Cheat Sheet

Quick-reference for hooks, state management, and lifecycle patterns in functional components.

## Modern Hooks & Patterns

### 1. State Management (`useState`)
```jsx
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  // Always use functional updates if next state depends on previous state
  const increment = () => setCount(prev => prev + 1);

  return <button onClick={increment}>Count: {count}</button>;
}
```

### 2. Side Effects (`useEffect`)
```jsx
import { useState, useEffect } from 'react';

function UserProfile({ userId }) {
  const [user, setUser] = useState(null);

  useEffect(() => {
    let active = true;

    async function loadData() {
      const data = await fetchUserData(userId);
      if (active) setUser(data);
    }
    loadData();

    // Clean up effect to prevent setting state on unmounted component
    return () => { active = false; };
  }, [userId]); // Dependency array: triggers whenever userId changes
}
```

---

## ⚠️ Common Pitfalls & Anti-Patterns

> [!WARNING]
> React lifecycle missteps can cause infinite loops, state sync lags, and stale closure bugs.

### 1. Modifying State Directly
Never modify state variables directly. Always use the setter function:
```jsx
// BAD: React won't detect changes and trigger a re-render
const [profile, setProfile] = useState({ name: 'Sahid', role: 'Dev' });
profile.name = 'John'; 

// GOOD: Triggers a fresh state snapshot
setProfile(prev => ({ ...prev, name: 'John' }));
```

### 2. Missing Unique Keys
Always provide a unique, persistent key when mapping arrays:
```jsx
// BAD: Index keys can cause UI glitches when lists are re-ordered/filtered
items.map((item, index) => <li key={index}>{item.title}</li>);

// GOOD: Uses stable database or model IDs
items.map(item => <li key={item.id}>{item.title}</li>);
```

---

## Authoritative Documentation
- [React Official Documentation (New Docs)](https://react.dev)
- [Beta React: Thinking in React](https://react.dev/learn/thinking-in-react)
