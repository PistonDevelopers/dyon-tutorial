# Continue

The `continue` keyword goes to the next turn.

```rust
loop {
    sleep(1)
    continue
    println("hi") // never called
}
```

To go to the next turn of an outer loop, use a label:

```rust
'outer: loop {
    loop {
        continue 'outer
    }
}
```
