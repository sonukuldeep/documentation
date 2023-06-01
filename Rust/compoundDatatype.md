---
parent: Rust
layout: home
title: Compound datatype
---

## Compound datatypes

1. Array
- Continuous group of items
- fixed length
- Length known at compile time
- homogeneous

Syntax:-
```rs
let array: [u32; 3] = [1,2,3];

let first_item = array[0];
let will_warn = array[100]; // compiler will warn while at runtime it will crash
```

2. Tuples
- Linear group of items
- fixed length
- length known at compile time
- heterogenous
- Empty tuple is called unit

```rs
let tuple: (bool, u16, u8) = (true, 2, 3);

let first_item = tuple.0;
let error = tuple.100; // will give error