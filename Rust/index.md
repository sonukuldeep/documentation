---
layout: home
title: Rust
has_children: true
---

# Rust

[main image](wsrv.nl/?url=rust-lang.org/static/images/rust-social-wide.jpg&w=600)

Rust is a modern systems programming language known for its focus on safety, performance, and concurrency. It was developed by Mozilla Research and first released in 2010. 

## Installation
[link](https://www.rust-lang.org/learn/get-started)

# Cargo
Cargo is the Rust build tool and package manager

When you install Rustup you’ll also get the latest stable version of the Rust build tool and package manager, also known as Cargo. Cargo does lots of things:

- build your project with cargo build
- run your project with cargo run
- test your project with cargo test
- build documentation for your project with cargo doc
- publish a library to crates.io with cargo publish

To test that you have Rust and Cargo installed, you can run this in your terminal of choice:
```rs
cargo --version
```

## Generate new project
```rs
cargo new hello-rust
```

## Compile, generate and run rust executable
```rs
cargo run
```