# Error handling

In Dyon, error handling use the `?` operator to propagate errors.

```rust
fn try_divide(a: f64, b: f64) -> res[f64] {
    return if b == 0 { err("Division by zero") }
           else { ok(a / b) }
}

fn foo(b: f64) -> res {
    a := try_divide(5, b)?
    return ok(a + 2)
}

fn main() {
    println(foo(2)) // prints `ok(4.5)`
    println(foo(0)) // prints `err("Division by zero")`
}
```

When using `unwrap`, an error is reported with a trace of all `?` operations:

```rust
println(unwrap(foo(0)))
```

```
--- ERROR ---
main (source/test.dyon)
unwrap

Division by zero
In function `foo` (source/test.dyon)
7,10:     a := try_divide(5, b)?
7,10:          ^

15,20:     println(unwrap(foo(0)))
15,20:                    ^
```

An `opt` is converted into `res` when using `?`,
with the error "Expected `some(_)`, found `none()".
