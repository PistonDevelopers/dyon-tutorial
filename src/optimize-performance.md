# Optimize performance

To optimize the performance of Dyon programs, compile with `cargo build --release`.

You can also get further optimization by disabling the default `debug_resolve` feature.
This compares location of variables on the stack with the static location.
It is not needed for running programs, but used to detect bugs in Dyon.

To disable `debug_resolve`, change the "Cargo.toml":

```
[dependencies.dyon]
version = "0.8.0"
features = []
```
