# Threads

In Dyon, a thread is created with the `go` keyword.
The type is `thr`, which defaults to `thr[any]`.

```rust
fn find_sum(n: f64) -> f64 {
    return sum i n { i + 1 }
}

fn main() {
    a := go find_sum(1_000_000)
    println(unwrap(join(thread: a))) // prints `500000500000`
}
```

A thread runs in parallel.

### Current objects are not passed between threads

Dyon does a clone of variables that are passed to a `go` call.
The new thread starts with an empty stack.
This means that current objects are not shared between threads.

### There can only be one reference when joining

A thread must only have a single reference to it when joining.
For example, if you store threads in an an array, you need to use `pop`.

Source code: [examples/multi_threads](https://github.com/PistonDevelopers/dyon-tutorial/tree/master/examples/multi_threads)

```rust
foo(i) = i + 40

fn main() {
    a := sift i 3 {go foo(i)}
    for i len(a) {
        println(unwrap(join(thread: pop(mut a))))
    }
}
```

### Some useful functions

- `fn join__thread(thr[any]) -> res[any]` - waits for the thread to finish, then returns the result
