---
layout: home
parent: Rust
title: Collection
---

## Collection

In Rust, collections are data structures that allow you to store and manipulate multiple values. Rust's standard library provides several collection types, each with its own characteristics and use cases.

Here are some of the commonly used collection types in Rust:

- Vec (Vector): A dynamically resizable array-like structure that allows you to store a variable number of elements of the same type. Vectors are efficient for random access and provide methods for adding, removing, and modifying elements.
- VecDeque (Double-Ended Queue): Similar to Vec, but with the ability to efficiently add and remove elements from both ends of the collection. It is useful for scenarios where elements need to be inserted or removed from the front or back frequently.
- HashMap<K, V>: A collection of key-value pairs where each key is unique. It provides fast lookup and insertion based on the keys. The keys and values can be of different types, and the ordering of the elements is not guaranteed.
- BTreeMap<K, V>: Similar to HashMap<K, V>, but it maintains the elements in sorted order based on the keys. It is implemented as a balanced binary search tree, which allows efficient range queries.
- HashSet: A collection of unique elements without any specific ordering. It provides fast lookup and insertion based on the elements. The elements must implement the Eq and Hash traits.
- BTreeSet: Similar to HashSet, but it maintains the elements in sorted order. It is implemented as a balanced binary search tree, allowing efficient range queries.
- LinkedList: A doubly linked list where each element is connected to the previous and next element. It allows efficient insertion and removal at both ends but is slower for random access compared to vector-like structures.
- String: As discussed earlier, String represents an owned, growable, UTF-8 encoded string. It provides methods for manipulating and working with string data.

These collection types provide a range of options to handle different scenarios. Rust's ownership and borrowing system ensures memory safety and efficient resource management when working with collections.

Example of Vec and Hashmap:-
```rs
use std::collections::HashMap;

fn main() {
    // Example with Vec<T>
    let mut numbers: Vec<i32> = Vec::new(); // Creating an empty vector

    numbers.push(10); // Adding elements to the vector
    numbers.push(20);
    numbers.push(30);

    println!("Vector: {:?}", numbers); // Printing the vector

    let first_element = numbers[0]; // Accessing an element by index
    println!("First element: {}", first_element);

    let length = numbers.len(); // Getting the length of the vector
    println!("Length: {}", length);

    // Example with HashMap<K, V>
    let mut scores: HashMap<String, i32> = HashMap::new(); // Creating an empty HashMap

    scores.insert(String::from("Alice"), 100); // Adding key-value pairs to the HashMap
    scores.insert(String::from("Bob"), 85);
    scores.insert(String::from("Charlie"), 92);

    println!("HashMap: {:?}", scores); // Printing the HashMap

    let alice_score = scores.get("Alice"); // Accessing a value by key
    match alice_score {
        Some(score) => println!("Alice's score: {}", score),
        None => println!("Alice's score not found"),
    }

    scores.remove("Bob"); // Removing a key-value pair from the HashMap

    for (name, score) in &scores { // Iterating over the HashMap
        println!("Name: {}, Score: {}", name, score);
    }
}
```