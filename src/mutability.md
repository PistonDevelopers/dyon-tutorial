# Mutability

In Dyon, when a function changes an argument, you need to add `mut`:

```rust
fn foo(mut x) {
    x = 3
}

fn main() {
    a := 2
    foo(mut a)
    println(a) // prints `3`
}
```

A function that calls a function that changes an argument, also need `mut`:

```rust
fn foo(mut x) {
    x = 3
}

// Requires `mut x` because it calls `foo`.
fn bar(mut x) {
    foo(mut x)
}

fn main() {
    a := 2
    bar(mut a)
    println(a) // prints `3`
}
```

This helps programmers understand the code.

Mutability information is part of the function name.
You can declare multiple functions with different mutability patterns:

```rust
// `name`
name(person: {}) = clone(person.name)

// `name(mut,_)`
fn name(mut person, name) {
    person.name = clone(name)
}

fn main() {
    character := {name: "Homer Simpson"}
    println(name(character)) // prints `Homer Simpson`
    name(mut character, "Marge Simpson")
    println(name(character)) // prints `Marge Simpson`
}
```
