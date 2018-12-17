# Command-line arguments

Dyon has a function to return an array of command-line arguments:

```rust
fn print_args_list {
    println(args_os())
}
```

The first item is the path of the executable.
