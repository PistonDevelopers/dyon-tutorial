# Break

The `break` keyword exits a loop:

```rust
a := 4
loop {
    a -= 1
    if a < 0 { break }
}
```

To exit an outer loop, use a label:

```rust
'outer: loop {
    loop {
        break 'outer
    }
}
```
