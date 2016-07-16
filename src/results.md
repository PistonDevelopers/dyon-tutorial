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

Result is used to handle errors explicitly.
Dyon has an operator `?` to make this easier.
You can read more about this in the chapter "Error handling".

### Some useful functions

- `fn unwrap(any) -> any`
- `fn unwrap_err(any) -> any`
- `fn is_ok(res[any]) -> bool`
- `fn is_err(res[any]) -> bool`
- `fn ok(any) -> res[any]`
- `fn err(any) -> res[any]`
