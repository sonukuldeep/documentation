---
parent: Rust
title: Struct
layout: home
---
## Struct
Use the keyword struct followed by a name in order to create a struct

    A type that's composed of other types
    Can contain different types
    It is further divided into 3 types
       - Classic
       - Tuple
       - Unit

### Classic structs

- Most commonly used
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
