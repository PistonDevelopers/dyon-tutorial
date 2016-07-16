# Results

In Dyon, results are wrapped in `ok(x)` or `err(x)`.
The type is `res` which defaults to `res[any]`.
The error type is always `any`.

```rust
fn main() {
    a := ok(5)
    if is_ok(a) {
        println(unwrap(a)) // prints `5`
    }
}
```
