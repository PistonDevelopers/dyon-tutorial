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
