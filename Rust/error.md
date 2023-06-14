---
layout: home
parent: Rust
title: Error handling
---

## Error handline
- Panic
- Option
- Result

1. Panic Simplest way to handle errors

What happens when a panic is encountered?

- Failure message is printed
- Program unwinds and cleans up the Stack
- Program quits


Should only be used when program comes to an unrecoverable state

Syntax:-
```rs
panic!("Farewell");

let v = vec![0, 1, 2, 3];
println!("{}", v[6]); // This will cause a panic
```

2. Option enum
- Manages the possibility of none existent values
- Type T is generic and associated with the Some variant.
- None indicates that no element was found.
- Some means that an element of type T was found

Syntax:-
```rs
enum Option<T> {
    None,
    Some(T),
}
```

3. Result enum
- Used for input/output operations (I/O)
    - Parsing strings
    - File access
    - Data validation
- Best for expected failures

Syntax:-
```rs
fn main() {
    enum Result<T, E> {
        Ok(T),
        Err(E),
    }
}
```

- Used for recoverable errors that are more common
- The Ok(T) variant represents a success and contains a value
- The Err(E) variant represents an error

> Unwrap and Expect
- Helper methods Of the Result type
- Unwrap returns the value inside the Ok variant. Returns a panic! macro for the Err variant.
- Expect returns a value or called the panic! macro with a detailed error message

```rs
fn main() {
    // ok
    File::open("hello.txt").unwrap();

    // Err
    File::open("hello.txt").expect("Failed to open hello.txt");
}
```
    
> The ? operator
- Similar to a match statement
- For Result type:
    - Unwraps the value if 0k variant
    - Returns an error if Err variant.
- For Option type:
    - Returns a value is with the Some variant
    - Returns nothing for the None variant

