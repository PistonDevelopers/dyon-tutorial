# Mutability interop

Mutability information is part of the function name:

```rust
fn foo(mut a: f64, b: f64) { ... }
```

The name of this function is `foo(mut,_)`.

```rust
module.add(Arc::new("foo(mut,_)".into()), foo, Dfn {
      lts: vec![Lt::Default; 2],
      tys: vec![Type::F64; 2],
      ret: Type::Void
  });
```
