# In-types

In Dyon, an in-type receives input data from a function.

The `in` keyword creates a receiver channel:

```rust
x := in log
```

Next time you call `log`, the input data is sent to `x`:

```rust
fn log(a: f64) {}

fn main() {
    x := in log
    log(1)
    println(next(x)) // Prints `some([1])`
}
```

### Calling functions

The type is `in[[]]` since arguments are stored in array:

```rust
fn log(a: f64) {}

fn foo(x: in[[f64]]) {println(next(x))}

fn main() {
    x := in log
    log(1)
    foo(x)
}
```

### Working With Threads

In-types works across threads:

```rust
fn log(a: f64) {}

fn finish() {}

fn bar(id: f64, n: f64) -> bool {
    for i n {
        log((id + 1) * 1000 + i)
        sleep(0.1)
    }
    finish()
    return true
}

fn main() {
    log := in log
    finish := in finish
    n := 10
    for i n {_ := go bar(i, 2)}
    loop {
        for msg in log {println(msg[0])}
        if n == 0 {break}
        for done in finish {n -= 1}
    }
}
```

Notice that `n == 0` is checked after emptying the log for messages.

### Other functions for in-types

- `fn next(channel: in) -> opt[any]` - Blocks thread until message is received from channel.
- `fn try_next(channel: in) -> opt[any]` - Checks for message on channel.
