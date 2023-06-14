---
layout: home
parent: Rust
title: Ownership
---

## Ownership

Ownership is a core concept in Rust that governs how memory is managed and ensures memory safety without the need for a garbage collector or runtime overhead. It revolves around the idea that every value in Rust has a single owner at any given time.

When you create a value in Rust, such as a variable or an object, you become its owner. As an owner, you have full control over that value and its associated memory. Ownership comes with three fundamental rules:

1. Unique Ownership:

- Each value in Rust has a unique owner, and there can only be one owner at a time.
- The owner is responsible for the memory deallocation when the value goes out of scope.
- When the owner goes out of scope, the value is dropped, and its memory is automatically freed.

2. Move Semantics:

- Ownership in Rust follows the move semantics by default.
- When a value is assigned to another variable or passed as a function argument, the ownership is transferred.
- The original owner loses its ownership, and the new owner takes control of the value.
- This prevents multiple variables from accidentally accessing and modifying the same value, reducing bugs and data races.

3. Borrowing and References:

- To allow temporary access to a value without transferring ownership, you can use borrowing and references.
- Borrowing enables you to lend a reference to a value to another part of your code.
- References come in two forms: immutable references (&T) and mutable references (&mut T).
- Borrowing enforces strict rules at compile-time to prevent data races, dangling references, and use-after-free errors.

These ownership rules enable the Rust compiler to perform static analysis and memory management at compile time. It ensures that values are dropped when they are no longer needed and prevents common issues like memory leaks and use-after-free bugs. The ownership system allows Rust to provide memory safety and concurrency guarantees without the need for manual memory management or garbage collection.

Rust's ownership model may seem strict at first, but it promotes clear ownership semantics, eliminates many runtime errors, and guarantees thread safety without sacrificing performance. It enables you to write robust, efficient, and safe code in a systems programming language.

Check docs for detailed explaination
[docs](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html)