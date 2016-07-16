# Dynamic modules

In Dyon, you organize code by using dynamic modules.
It is common to write a loader script that loads modules and imports them to
other modules.

### Dynmod example

Source: [examples/dynmod](https://github.com/PistonDevelopers/dyon-tutorial/tree/master/examples/dynmod)

main.dyon:
```rust
fn main() {
    math := unwrap(load("src/math.dyon"))
    game := unwrap(load(source: "src/game.dyon", imports: [math]))
    call(game, "main", [])
}
```

math.dyon:
```rust
add(a: f64, b: f64) = a + b
```

game.dyon:
```rust
fn main() {
    a := 2
    b := 3
    println(add(a, b)) // prints `5`
}
```

### Calling functions in dynamic modules

Dyon peforms a runtime lifetime check of arguments for these functions:

- `fn call(module, name, args)` - returns no value
- `fn call_ret(module, name, args)` - returns value

### Why dynamic modules?

Module loading is often an important part of a program:

- Download updates
- Refresh game logic for interactive programming
- Swap between backends

For example, the same Dyon game can run on game engines that supports multiple backend APIs for rendering.
In other languages you might write generic code to make it reusable across APIs.
Dyon solves this by making all code reusable across APIs, as long as the
dependencies implements the same set of functions.
