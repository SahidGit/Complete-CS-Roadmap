# 🎯 Week 52: Rust Systems Programming

> **Duration:** 24 hours | **Difficulty:** 🔴 Advanced | **Prerequisites:** Basic programming syntax, Week 51

## 📌 Goal
Learn the Rust programming language, master memory ownership, manage references and borrowing, understand traits, and write performant system tools.

---

## 🎓 Learning Objectives
By the end of this week, you will:
- ✅ Master Rust's Ownership model (stack vs heap memory allocation)
- ✅ Understand Borrowing (immutable references vs single mutable references)
- ✅ Resolve compile-time lifetime references (`'a`)
- ✅ Use Structs, Enums, and pattern matching (`match`)
- ✅ Implement Traits to establish shared behaviors
- ✅ Manage packages and dependencies using Cargo
- ✅ Handle errors using the `Result` and `Option` types

---

## 📚 Prerequisites & Study Hours
- **Prerequisites**: Week 21 (Algorithms), basic C++ or JavaScript syntax.
- **Estimated Study Hours**: 24 hours
- **Difficulty**: 🔴 Advanced

---

## 📖 Concepts & Theory

### 1. The Borrow Checker
Rust achieves memory safety at compile time without a Garbage Collector by enforcing strict borrowing rules:
1. You may have any number of immutable references (`&T`) to a resource.
2. You may have exactly one mutable reference (`&mut T`) to a resource in a scope.
3. You cannot have both immutable and mutable references to the same resource simultaneously.

```
Owner (x) ────► [ Data in Memory ]
  │
  ├─► Borrow &x  (Read-only, multiple allowed)
  │
  └─► Borrow &mut x (Read/Write, exactly one allowed, no others active)
```

### 2. Match Pattern Matching & Enums
Enums in Rust are algebraic data types, allowing variant payloads:

```rust
enum WalletState {
    Active(String), // holds address
    Locked,
    Empty,
}

fn process_wallet(state: WalletState) {
    match state {
        WalletState::Active(addr) => println!("Connected to wallet: {}", addr),
        WalletState::Locked => println!("Wallet is locked. Enter password."),
        WalletState::Empty => println!("Initialize wallet seed phrase first."),
    }
}
```

---

## 💻 Daily Study Plan

### 📅 Monday: Cargo & Ownership
- Learn Cargo project initialization (`cargo new`, `cargo run`, `cargo build`).
- Understand stack vs heap allocation. Master ownership transfers (move semantics).

### 📅 Tuesday: Borrowing & References
- Practice writing code that passes references to functions.
- Master borrow checker constraints (debugging common compiler errors).

### 📅 Wednesday: Lifetimes
- Learn why compiler needs explicit lifetimes when functions return references.
- Implement structures containing referenced fields.

### 📅 Thursday: Structs, Enums & Error Handling
- Write custom Structs and implement methods using the `impl` block.
- Study error propagation using `Result<T, E>` and `?` operators.

### 📅 Friday: Projects Implementation
- Build the **CLI File Organizer** and **Rust HTTP Server** projects.

### 📅 Saturday: Labs & Compilation Exercises
- Complete standard Rust exercises (like Rustlings).

### 📅 Sunday: Revision & Interview Prep
- Review reference lifetimes and smart pointers (`Box`, `Rc`, `RefCell`).

---

## 🧪 Projects & Implementation Guide

### Project 1: Multi-Threaded HTTP Server
- **Architecture**: A low-level TCP sockets listener in Rust using a thread pool to dispatch and process requests in parallel.
- **Folder Structure**:
  ```
  http-server/
  ├── Cargo.toml
  └── src/
      ├── main.rs
      └── threadpool.rs
  ```
- **Implementation Guide**: Listen using `std::net::TcpListener`, parse requests, and write standard HTTP headers/responses back to the stream.

### Project 2: CLI File Organizer
- **Architecture**: App traversing folders, sorting files by extensions using pattern matching.

### Project 3: Password Hash Vault
- **Architecture**: CLI tool storing credentials in an encrypted file.

---

## 📝 Practice Exercises
1. Implement a function that takes a string reference and returns its first word length without moving ownership.
2. Design a custom `Shape` trait and implement it on `Circle` and `Rectangle` structures.
3. Write a file reader that catches missing file exceptions using the `Result` enum instead of crashing the system.
4. Implement a custom thread pool dispatcher in Rust that processes 10 tasks in parallel.

---

## 💼 Interview Questions & Answers
- **Q**: What is the difference between `String` and `&str` in Rust?
- **A**: `String` is a growable, heap-allocated, owned sequence of UTF-8 bytes. `&str` is an immutable, stack-allocated slice referencing a sequence of UTF-8 bytes stored elsewhere (either on the heap, stack, or statically in execution memory).

---

## 📖 Official Resources
- [The Rust Programming Language Book](https://doc.rust-lang.org/book/)
- [Rust by Example Tutorial](https://doc.rust-lang.org/rust-by-example/)
