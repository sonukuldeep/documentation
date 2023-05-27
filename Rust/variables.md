---
title: Variables
layout: home
parent: Rust
---

## Variables

Certainly! Here's a description of `let`, mutability, shadowing, and `const` in Rust, each explained in separate points:

1. `let`:
   - The `let` keyword is used to create variables in Rust.
   - Variables created with `let` are immutable by default, meaning their values cannot be changed once assigned.
   - The type of the variable can be inferred by the compiler based on the assigned value, or it can be explicitly specified using type annotations.
   - Syntax: `let variable_name = value;`

    1. Mutability:
       - Rust promotes a default pattern of immutability for variables to ensure safer and more predictable code.
       - To create mutable variables, you need to explicitly declare them as mutable using the `let mut` syntax.
       - Mutable variables allow changing their values after assignment.
       - Syntax: `let mut variable_name = value;`
    
    2. Shadowing:
       - Shadowing is the process of creating a new variable with the same name as an existing variable, effectively "shadowing" the original variable.
       - Shadowing allows you to reuse variable names while changing their type or value.
       - It is different from mutability because it creates a new variable rather than modifying the existing one.
       - Shadowed variables can have different types, allowing flexibility in the program.
       - Syntax: `let variable_name = new_value;`

2. `const`:
   - Constants are values that are not allowed to change throughout the execution of a program.
   - Constants are always immutable, and their values must be known at compile-time.
   - They are declared using the `const` keyword and require explicit type annotations.
   - Constants are typically written in uppercase with underscores separating words.
   - Syntax: `const CONSTANT_NAME: Type = value;`

It's important to note that `let` and `const` are used for creating variables, while mutability and shadowing determine how the variables can be modified or reassigned.