---
layout: home
title: Loops
parent: Rust
---

## Loop

1. loop It is used to execute over a blockof code forever. Or until it is stopped, or the program quits.

syntax:-
```rs
loop {
    println!("I loop forever!");
}
```

2. break syntax:-
```rs
loop {
    println!("Stops when program hits break!");
    break;
}
```
    
3. While loop syntax:-
```rs
let mut number = 3;
while number != 0 {
    println!("{}", number);
    number -= 1;
}
println!("End of while");
```

4. for loop syntax:-
```rs
let a = [10, 20, 30, 40, 50];
for element in a.iter() {
    println!("The value is: {}", element);
}
```