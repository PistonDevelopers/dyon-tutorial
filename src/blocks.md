# Blocks

A block starts with `{` and ends with `}`:

```rust
a := {
    println("hi!")
    5
}
println(a) // prints `5`
```

The last expression in a block becomes the result of block expression.

When declaring a variable inside a block, you might get an error:

```rust
a := {
    b := 5
    b // ERROR
}
```

```
--- ERROR ---
In `source/test.dyon`:

`b` does not live long enough
2,10:     a := {
2,10:          ^
3,1:         b := 5
4,1:         b // ERROR
5,1:     }
```

Dyon has no garbage collector, but uses a lifetime checker instead.
This is explained later in the chapter "Lifetimes".

This means that "b" only lives for the scope of the block,
and you must use `clone` to fix it:

```rust
a := {
    b := 5
    clone(b) // OK
}
```

When you do a math operation, Dyon knows it is safe:

```rust
a := {
    b := 5
    b + 2 // OK
}
```
