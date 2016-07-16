# Current objects

In Dyon, a current object is a variable that can be accessed by name.

To create a current object, use `~` when declaring a variable:

```rust
fn main() {
    ~ list := [1, 2, 3]
    print_list()
}

// Get the current object with name `list`.
fn print_list() ~ list {
    for i { println(list[i]) }
}
```

A new current object overrides the old one until it runs out of scope:

```rust
fn main() {
    ~ a := 2
    foo() // prints `2`
    {
        ~ a := 3
        foo() // prints `3`
    }
    foo() // prints `2`
}

fn foo() ~ a {
    println(a)
}
```
