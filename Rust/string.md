---
title: String
layout: home
parent: Rust
---

## String
Rust treats strings differently compared to other languages

- Strings are represented by the String type which is part of the Rust standard library and provides methods for string manipulation and operations.
- Rust strings are growable, meaning their length can change dynamically.
- Strings are encoded as UTF-8, allowing for handling and manipulation of Unicode characters.
- The String type is heap-allocated, meaning the memory for the string content is dynamically allocated on the heap.
- Rust provides seamless conversion between string slices (&str) and owned strings (String).
- String manipulation methods like concatenation, appending, slicing, replacing, and more are available for working with strings.

Creating a new String can be done using the String::new() function, which returns an empty string. You can also create a String from a string literal using the to_string() method or the String::from() function:

```rs
let empty_string = String::new();
let hello = "Hello, ".to_string();
let world = String::from("world!");
```

The String type supports concatenation using the + operator or the String::push_str() method:
```rs
let hello = "Hello".to_string();
let world = "world!";
let hello_world = hello + " " + world;

let mut message = String::from("Hello, ");
let name = "Alice";

message.push_str(name);

println!("{}", message); // Output: Hello, Alice
```

Additionally, you can use the format!() macro to concatenate multiple values into a String:
```rs
let name = "Alice";
let age = 25;
let message = format!("My name is {} and I am {} years old.", name, age);
```

Rust's String type provides many other useful methods for manipulating and working with strings, such as indexing, slicing, replacing, splitting, and more. You can explore these methods in the Rust documentation or by using Rust's built-in documentation tool (rustup doc or cargo doc).

It's important to note that Rust distinguishes between string slices (&str) and owned strings (String). String slices are borrowed references to string data, and they can be used for efficient string manipulation when ownership is not required. Rust provides seamless conversion between string slices and String using the &str and String types' respective as_str() and into() methods.

```rs
fn print_string_length(string: &str) {
    println!("Length of the string: {}", string.len());
}

fn main() {
    // Converting String to &str
    let owned_string = String::from("Hello, Rust!");
    let borrowed_string: &str = owned_string.as_str();

    print_string_length(borrowed_string);

    // Converting &str to String
    let borrowed_string = "Hello, Rust!";
    let owned_string: String = borrowed_string.to_string();

    println!("New owned string: {}", owned_string);
}
```
