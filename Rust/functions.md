---
layout: home
parent: Rust
title: Function
---

## Function
- Argument type is always required
- Return type is required if value is returned
- If no value is retured, return type is unit

Syntax:-
```rs
fn function_name(argument: argumentType) -> returnType {
    //body
}
```

Example:-
```rs
fn change_to_upper_case(input: String) -> String {
    let mut output = input.to_uppercase();
    output.push('!');
    output // mark missing semi-colon which tell the compiler to return this
}

let output = change_to_upper_case("Hello world");
```

## Some common function, there syntax and example

1. `println!`:
   - Description: Macro for printing formatted text to the console.
   - Syntax: `println!("format string", arg1, arg2, ...);`
   - Example:
     ```rust
     let name = "Alice";
     let age = 25;
     println!("Hello, {}! You are {} years old.", name, age);
     ```

2. `String::from`:
   - Description: Creates a new heap-allocated `String` from a string literal or another `String`.
   - Syntax: `let s = String::from("string literal");`
   - Example:
     ```rust
     let s = String::from("Hello");
     ```

3. `vec!`:
   - Description: Macro for creating a new `Vec` (vector) with initial values.
   - Syntax: `let v = vec![val1, val2, ...];`
   - Example:
     ```rust
     let v = vec![1, 2, 3];
     ```

4. `Option::Some` and `Option::None`:
   - Description: Represents the presence or absence of a value.
   - Syntax:
     ```rust
     let x: Option<Type> = Some(value);
     let y: Option<Type> = None;
     ```
   - Example:
     ```rust
     let x: Option<i32> = Some(5);
     let y: Option<i32> = None;
     ```

5. `Result::Ok` and `Result::Err`:
   - Description: Represents the success or failure of a computation, often used for error handling.
   - Syntax:
     ```rust
     let result: Result<OkType, ErrType> = Ok(value);
     let result: Result<OkType, ErrType> = Err(error);
     ```
   - Example:
     ```rust
     let result: Result<i32, String> = Ok(42);
     let error: Result<i32, String> = Err("Something went wrong".to_string());
     ```

6. `match`:
   - Description: Control flow construct for pattern matching and executing code based on matched patterns.
   - Syntax:
     ```rust
     match variable {
         pattern1 => {
             // code to execute when pattern1 matches
         }
         pattern2 => {
             // code to execute when pattern2 matches
         }
         // ...
     }
     ```
   - Example:
     ```rust
     let x: Option<i32> = Some(5);
     match x {
         Some(value) => {
             println!("Got a value: {}", value);
         }
         None => {
             println!("No value");
         }
     }
     ```

