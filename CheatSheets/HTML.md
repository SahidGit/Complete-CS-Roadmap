# HTML Cheat Sheet

HTML5 structure, semantic elements, and accessibility best practices.

## Safe & Semantic Structure

### 1. Document Layout
Always structure your layouts with semantic HTML5 elements to ensure accessibility (a11y) and SEO optimization:
```html
<header role="banner">
  <nav aria-label="Main Navigation">
    <!-- Links go here -->
  </nav>
</header>

<main id="main-content">
  <section aria-labelledby="section-title">
    <h2 id="section-title">Latest Updates</h2>
    <article>
      <h3>Article Title</h3>
      <p>Content goes here...</p>
    </article>
  </section>
</main>

<footer role="contentinfo">
  <p>&copy; 2026 OpenCS</p>
</footer>
```

### 2. Forms and Accessibility
Ensure every input has a matching `<label>` or descriptive label attributes:
```html
<!-- Explicit labeling -->
<label for="email-address">Email Address</label>
<input type="email" id="email-address" name="email" required>

<!-- Accessibility links -->
<a href="#main-content" class="skip-link">Skip to main content</a>
```

---

## ⚠️ Common Pitfalls & Anti-Patterns

> [!WARNING]
> Using wrong tag semantics breaks accessibility tree maps and degrades SEO scoring.

### 1. Div-itis (Lack of Semantics)
Avoid making everything a `<div>` or `<span style="font-weight:bold">`:
```html
<!-- BAD: Inaccessible list of clickables -->
<div class="my-button" onclick="submit()">Click Me</div>

<!-- GOOD: Native keyboard-focusable interactive element -->
<button type="button" class="btn" onclick="submit()">Click Me</button>
```

### 2. Heading Level Skips
Do not use `<h1>` through `<h6>` for visual sizing. Always maintain document hierarchy:
```html
<!-- BAD -->
<h1>Page Title</h1>
<h4>Sub-heading directly below title</h4> <!-- Skips h2 and h3 -->

<!-- GOOD -->
<h1>Page Title</h1>
<h2>Sub-heading</h2>
```

---

## Authoritative Documentation
- [MDN Web Docs: HTML (HyperText Markup Language)](https://developer.mozilla.org/en-US/docs/Web/HTML)
- [W3C Web Accessibility Initiative (WAI) Tutorials](https://www.w3.org/WAI/tutorials/)
