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

In a mathematical loop, `break` skips the rest:

```rust
fn main() {
    list := [1, 2, 3]
    println(sum i {
        if i > 1 { break } // skip `3`
        list[i]
    }) // prints `3`
}
```
