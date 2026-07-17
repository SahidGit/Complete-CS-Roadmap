# CSS Cheat Sheet

Cascading Style Sheets layouts, responsiveness variables, and selectors.

## Core Layout Patterns

### 1. CSS Custom Properties (Variables)
Declare theme tokens at the root level for easy maintenance:
```css
:root {
  --primary: #6e56cf;
  --bg: #050505;
  --transition-fast: 0.2s cubic-bezier(0.4, 0, 0.2, 1);
}

.element {
  background-color: var(--bg);
  color: var(--primary);
  transition: transform var(--transition-fast);
}
```

### 2. Flexbox (One-Dimensional Layouts)
```css
.flex-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  gap: 16px;
  flex-wrap: wrap; /* Wraps items cleanly on smaller viewports */
}
```

### 3. Grid (Two-Dimensional Layouts)
```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 20px;
}
```

---

## ⚠️ Common Pitfalls & Anti-Patterns

> [!WARNING]
> Abusing cascading hierarchy and layout properties can break fluid layouts and layout performance.

### 1. Specificity Overrides (`!important`)
Avoid using `!important` as a quick fix to override styling.
```css
/* BAD: Overrides cascade specificity permanently */
.btn { color: white !important; }

/* GOOD: Refine target selectors or specificity hierarchy */
.card .btn { color: white; }
```
*Why it's dangerous:* `!important` makes debugging styles extremely difficult because it overrides standard specificity.

### 2. Hardcoded Dimensions
Avoid setting hard widths or heights that can overflow containers:
```css
/* BAD: Breaks layout on screens narrower than 400px */
.card { width: 400px; }

/* GOOD: Adapts dynamically to viewport */
.card { width: 100%; max-width: 400px; }
```

---

## Authoritative Documentation
- [MDN Web Docs: CSS (Cascading Style Sheets)](https://developer.mozilla.org/en-US/docs/Web/CSS)
- [CSS-Tricks: A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [CSS-Tricks: A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
