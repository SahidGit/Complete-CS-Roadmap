# 🦀 Rust Programming Reference

Rust is a multi-paradigm, general-purpose systems programming language designed for performance and safety, especially safe concurrency.

---

## 🏗️ Core Mechanics

### 1. Ownership & Memory Safety
Rust manages memory using a compile-time tracking system. It bypasses both garbage collection and manual memory management (`malloc`/`free`):
- Each value in Rust has an **owner**.
- There can only be **one owner** at a time.
- When the owner goes out of scope, the value is dropped (freed from memory).

### 2. Borrowing & References
Instead of transferring ownership, you can borrow values:
- You may have any number of **immutable references** (`&T`).
- You may have exactly **one mutable reference** (`&mut T`) in a scope.
- *The Borrow Checker*: References must always be valid (they cannot outlive their owners).

```rust
fn main() {
    let mut s = String::from("hello");
    
    let r1 = &s; // Immutable borrow
    let r2 = &s; // OK
    println!("{} and {}", r1, r2);
    
    let r3 = &mut s; // Mutable borrow
    r3.push_str(", world"); // Modifies the value in place
    println!("{}", r3);
}
```

### 3. Traits & Generics
Traits define shared behavior in Rust, serving a similar role to interfaces in other languages:
```rust
pub trait Summary {
    fn summarize(&self) -> String;
}

pub struct Article {
    pub title: String,
    pub content: String,
}

impl Summary for Article {
    fn summarize(&self) -> String {
        format!("{}: {}", self.title, self.content)
    }
}
```

---

## 🔗 Official Documentation
- [The Rust Programming Language Book](https://doc.rust-lang.org/book/)
- [Rust By Example Guide](https://doc.rust-lang.org/rust-by-example/)
- [Solana Cookbook: Rust reference](https://solanacookbook.com/)
