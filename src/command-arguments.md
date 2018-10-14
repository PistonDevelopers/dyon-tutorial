# Command-line arguments

Dyon uses a function to return an array of arguments which the program
was started with:

```rust
fn print_args_list {
    println(args_os())
}
```

The first element is usually the path of the executable.
