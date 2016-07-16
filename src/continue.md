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

In a mathematical loop, `continue` skips the current item:

```rust
fn main() {
    list := [1, 2, 3, 4]
    println(sum i {
        if i == 2 { continue } // skip `3`
        list[i]
    }) // prints `7`
}
```
