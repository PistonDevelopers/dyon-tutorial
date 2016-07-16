# Secrets

In Dyon, a secret is a hidden array of values associated with a `bool` or `f64`.

Use `explain_why` to add a secret to a `bool`:

```rust
a := explain_why(true, "hi!")
if a {
    println(why(a)) // prints `["hi!"]`
}
```

Use `explain_where` to add a secret to a `f64`:

```rust
a := explain_where(2.5, "giant")
println(where(a)) // prints `["giant"]`
```

A secret propagates from the left argument of a binary operator:

```rust
a := explain_where(2.5, "giant")
is_tall := a > 2.0
if is_tall {
    println(why(is_tall)) // prints `["giant"]`
}
```

When using a `min`, `max`, `any` or `all`, the indices are automatically added as secrets:

```rust
list := [[1, 2], [3, 4]]
println(why(any i, j { list[i][j] > 2 })) // prints `[1, 0]`
```
