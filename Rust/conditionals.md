---
layout: home
parent: Rust
title: Conditionals 
---
### Conditionals

1. If
syntax: 
```rs
let price = 10;
if price > 0 {
    println!("Price is greater than zero");
}
```

2. If else 
syntax: 
```rs
let price = 10;
if(price > 0) {
    println!("Price is greater than zero");
} else {
    println!("Price less than or equal to zero");
}
```


3. If else if
syntax: 
```rs
let price = 10;
if(price > 0) {
    println!("Price is greater than zero");
} else if price == 0 {
    println!("Price equal to zero");
} else {
    println!("Price less than zero");
}
```

4. Match
- Rust provides pattern matching with the match keyword
- A scrutinee expression is provided to compare to the patterns.
- Arms are evaluated and compared with the scrutinee expression

syntax:-
```rs
let x = 1;
match x {
    1 => println!("one"),
    2 => println!("two"),
    3 => println!("three"),
    4 => println!("four"),
    5 => println!("five"),
    _ => println!("something else"),
}
```



