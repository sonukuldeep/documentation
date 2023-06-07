---
layout: home
title: Emum
parent: Rust
---

### Enums

Use the word enum folled by a name to create an enum

Enums
- An enum variant can include any kind of data
- An enum can have a variety of types
- List all variables of same data or of the same type
- Common feature across programming languages
- Referred to as algebric data types

Example:-
```rs
enum CardinalDirections {
    North,
    South,
    East,
    West,
}

let north = CardinalDirections::North;
let south = CardinalDirections::South;
let east = CardinalDirections::East;
let west = CardinalDirections::West;

// another way
enum CardinalDirections {
    North(String),
    South(String),
    East(String),
    West(String),
}

let west = CardinalDirections::West(String::from("West"));
```
