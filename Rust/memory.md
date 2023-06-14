---
layout: home
parent: Rust
title: Memory
---

## Memory
In rust memory is managed through a system of ownership with a set of rules that the compiler checks. If any of the rules are violated, the program won’t compile. None of the features of ownership will slow down your program while it’s running.

- Rust stores data in two differently structured parts of memory

1. Stack:

- The stack is a region of memory that is used for storing local variables and function call information.
- It operates on a Last-In, First-Out (LIFO) principle.
- Stack memory allocation and deallocation are managed automatically by the compiler.
- Stack allocations have a fixed size known at compile time.
- The lifetime of stack-allocated variables is determined by the scope in which they are defined.
- Stack memory is generally faster to allocate and deallocate than heap memory.

2. Heap:

- The heap is a region of memory used for dynamic memory allocation.
- It allows for the allocation of memory whose size is not known at compile time or that needs to outlive the scope it was created in.
- Heap memory allocation and deallocation are managed explicitly by the programmer.
- Heap allocations have a dynamic size and are requested using functions like Box::new(), Vec::new(), or via system APIs.
- Memory on the heap needs to be manually deallocated to prevent memory leaks.
- Heap memory access is generally slower than stack memory due to indirection and dynamic allocation overhead.
