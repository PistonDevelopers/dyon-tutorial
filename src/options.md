# Options

In Dyon, optional values are wrapped in `some(x)` or `none()`.
The type is `opt`, which defaults to `opt[any]`.

The `unwrap` function returns the value inside `some(x)`.

```rust
fn main() {
    a := some(5)
    if a != none() {
        println(unwrap(a)) // prints `5`
    }
}
```

### Note to programmers accustomed to `null`

Many languages uses `null` or `nil` to indicate an empty reference.
This leads to lots of maintenance problems, because it can appear anywhere.

Dyon uses `opt` whenever you would use `null` in another language.
This forces programmers to deal with it explicitly,
which reduces number of bugs in the program.

### Some useful functions

- `fn some(any) -> opt[any]`
- `fn none() -> opt[any]`
- `fn unwrap(any) -> any`
