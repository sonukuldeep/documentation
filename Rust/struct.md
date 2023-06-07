---
parent: Rust
title: Struct
layout: home
---

- Each field has a name and a type

2. Tuple
- Similar to classic structs
- Their fields have no names

3. Unit structs
- Have no field
- Similar to the () unit type

Syntax
```rs
struct Car {
    make: String
    model: String,
    Yeat: u32,
}

// instanciate a struct
let car1 = Car {
    make: String::from("Ford"),
    model: String::from("Mustang"),
    year: 1967,
}

car1.year // return year 
car1.make // return make
```
