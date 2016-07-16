# Copy-on-write

In Dyon, arrays and objects uses atomic reference counting (Arc).

Whenever there are two non-stack references to the same array,
it will create a copy when changing the array:

```rust
fn main() {
    // `[1, 2]` is inside an array,
    // and is therefore not stored in stack memory.
    a := [[1, 2]]
    // Create another reference to `[1, 2]`
    b := [a[0]]
    b[0][0] = 3
    println(b[0][0])
    // The old `[1, 2]` array remains unchanged.
    println(a[0][0])
}
```

This means that methods, the building-block of OOP patterns, are impossible to use in Dyon:

```rust
fn foo(mut a) {
    a[0] = 3
}

fn main() {
    // `[1, 2]` is inside an array,
    // and is therefore not stored in stack memory.
    a := [[1, 2]]
    // When we pass it as argument,
    // the reference counter is increased.
    foo(mut a[0])
    // The value remains unchanged,
    // because `foo` changed a copy.
    println(a[0][0]) // prints `1`
}
```

To modify variables inside other variables, it must be declared on the stack:

```rust
fn foo(mut a) {
    a[0] = 3
}

fn main() {
    // `[1, 2]` is put on the stack.
    list := [1, 2]
    // Putting a stack reference to `list` inside `a`
    a := [list]
    // When we pass it as argument,
    // the stack reference is passed.
    foo(mut a[0])
    // The value is changed.
    println(a[0][0]) // prints `3`
}
```

### Data oriented design

When writing programs in Dyon, you need to avoid copy-on-write.
The easiest way to do this is to organize application structure in flat arrays.

- Do not worry about having lots of arrays
- Use current objects to pass arrays around
- Batch changes to arrays together by iterating over them

Optimize the data structure for the algorithms that processes it.
When the algorithm changes, the data structure changes too!

### Dyon is a scripting language

If you need OOP patterns, then there is only one solution: Use another language, for example Rust.
Dyon is designed for scripting, as in solving problems fast.
It is not designed for building abstractions, or proving things through the type system.
