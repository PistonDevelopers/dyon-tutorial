# Threads

In Dyon, a thread is created with the `go` keyword:

```rust
fn find_sum(n: f64) -> f64 {
    return sum i n { i + 1 }
}

fn main() {
    a := go find_sum(1_000_000)
    println(unwrap(join(thread: a))) // prints `500000500000`
}
```
