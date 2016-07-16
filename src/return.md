# Return

In Dyon, `return` can be used as a variable:

```rust
fn foo(mut a: f64) -> {
    return = a + 2
    a += 2
}
```

If you leave out `=`, the function will exit with the value:

```rust
fn foo(a: f64) -> {
    return a + 2
    println("hi") // never gets called.
}
```

Functions without `->` can use `return` without a value:

```rust
fn foo() {
    return
}
```

All functions that returns a value must use `return`.
You get an error if you forget it:

```rust
fn foo(a: f64) -> { a + 2 } // ERROR
```

```
--- ERROR ---
In `source/test.dyon`:

Type mismatch (#775):
Expected `any`, found `void`
1,1: fn foo(a: f64) -> { a + 2 }
1,1: ^
```
