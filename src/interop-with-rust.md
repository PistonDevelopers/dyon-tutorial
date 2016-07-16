# Interop with Rust

Dyon is designed to work with Rust, but uses different types.

Rust uses static types only, which usually takes up less memory and runs faster.
When you need to high performance, it is recommended to use Rust.

### Functions example

Source: [dyon/examples/functions.rs](https://github.com/PistonDevelopers/dyon/blob/master/examples/functions.rs)

The `dyon_fn!` macro lets you write a Rust function that maps to Dyon types:

```rust
#[macro_use]
extern crate dyon;

dyon_fn!{fn say_hello() {
    println!("hi!");
}}
```

Add the function to a module:

```rust
module.add(Arc::new("say_hello".into()), say_hello, Dfn {
      lts: vec![],
      tys: vec![],
      ret: Type::Void
  });
```

The `Dfn` struct describes the type information of the function signature:

- `lts` - lifetimes, e.g. `Lt::Default`
- `tys` - types, e.g. `Type::F64`
- `ret` - return type, e.g. `Type::Bool`
