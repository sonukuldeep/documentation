---
layout: home
title: Borrowing
parent: Rust
---

## Borrowing

Borrowing is a fundamental concept related to ownership and memory management. It ensures that multiple parts of a program can access and manipulate data without causing issues like data races or memory leaks.

When you create a variable in Rust, you become its owner, meaning you have exclusive control over that variable and its memory. However, sometimes you need to temporarily share that variable with other parts of your code without transferring ownership. This is where borrowing comes into play.

Borrowing allows you to lend a reference to a variable or data structure to another part of your code, called the borrower, without giving up ownership. There are two types of borrowing in Rust: mutable borrowing and immutable borrowing.

1. Immutable Borrowing (Shared Reference):

- When you borrow a variable with an immutable borrow, you can read its value but cannot modify it.
- Immutable borrows are denoted using the & symbol. For example, &x borrows the variable x immutably.
- Multiple immutable borrows can exist simultaneously, allowing multiple parts of your code to read the data.
- The borrower can hold the reference for as long as it needs, but it cannot outlive the owner's lifetime.

2. Mutable Borrowing (Exclusive Reference):

- When you need to modify a borrowed variable, you use a mutable borrow.
- Mutable borrows are denoted using the &mut symbol. For example, &mut y borrows the variable y mutably.
- Rust enforces strict rules with mutable borrows. Only one mutable borrow can exist at a time for a specific piece of data within a given scope.
- Mutable borrows prevent simultaneous access to the data to avoid data races.
- The borrower can hold the mutable reference for as long as it needs, but it cannot outlive the owner's lifetime.

The Rust compiler statically analyzes your code to ensure that borrows adhere to these rules at compile time. This analysis prevents common issues like use-after-free errors, data races, and dangling references, which are typically found in languages with manual memory management.

Borrowing, combined with ownership, allows Rust to achieve memory safety without relying on a garbage collector or runtime overhead. It enables you to write efficient and safe code by enforcing strict rules around the ownership and usage of variables and data structures.
Check detailed Doc on borowwing [Doc](https://doc.rust-lang.org/book/ch04-02-references-and-borrowing.html)

Example:-
```rs
fn main() {
    // Immutable borrowing example
    let x = 5; // Original value

    // Borrowing x immutably with an immutable reference
    let y = &x;

    println!("x: {}", x);
    println!("y: {}", y);

    // Uncommenting the line below will result in a compilation error
    // x = 10; // Error: Cannot assign to `x` because it is borrowed

    // Mutable borrowing example
    let mut z = 10; // Original mutable value

    // Borrowing z mutably with a mutable reference
    let w = &mut z;

    println!("z: {}", z);
    println!("w: {}", w);

    *w += 5; // Modifying the value through the mutable reference

    println!("Modified z: {}", z);
    println!("Modified w: {}", w);
}
```