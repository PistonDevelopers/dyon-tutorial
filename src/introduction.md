# Introduction

Welcome to the Dyon 0.21 tutorial!

Dyon is a dynamically typed scripting language,
designed for game engines and interactive applications.
It was started in 2016 by Sven Nilsen.

This tutorial is written for people with little programming experience.
The language is made simple on purpose.
If you are experienced programmer, you might want to skip to the parts that interests you.

### Dyon is different!

If you have used another programming language before,
there are some things worth to keep in mind:

Dyon has a limited memory model because of the lack of a garbage collector.
The language is designed to work around this limitation.

The language takes ideas from Javascript, Go and Rust, but focuses on practical features for making games:

- Optional type system with ad-hoc types
- Similar object model to Javascript, but without `null`
- Built-in support for 4D vectors, HTML hex colors
- Go-like coroutines

There are plenty of new ideas in Dyon:

- Lifetime check for function arguments
- Use `return` as local variable
- Mathematical loops
- Current objects
- Secrets
- Grab expressions
- Dynamic modules as a way of organizing code

### How this tutorial is organized

At the bottom there is a "Comments" section.
This contains things you might have noticed and things you can try out on your own.

### Source code

You will find the source code for all examples under "examples" in the [git repository](https://github.com/pistondevelopers/dyon-tutorial).
