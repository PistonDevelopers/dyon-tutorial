# lib.dyon

When designing Dyon libraries written in Rust, it is common to include
a "lib.dyon" file in the "src" folder.
This file lists all external functions are they would appear in Dyon code.

Two examples from the Dyon library:

```rust
/// Returns an array of derived information for the truth value of `var`.
/// This can be used with the value of `∃`/`any` and `∀`/`all` loops.
fn why(var: bool) -> [any] { ... }

/// Returns an array of derived information for the value of `var`.
/// This can be used with the value of `min` and `max` loops.
fn where(var: f64) -> [any] { ... }
```

Comments should start with `///`.
