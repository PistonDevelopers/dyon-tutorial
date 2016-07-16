# Lifetime interop

The `Lt` enum describes the lifetime of an argument.

The most common lifetime is `Lt::Default` (no lifetime).

If you have a function like this:

```rust
fn foo(mut a: [{}], b: 'a {}) { ... }
```

Then the `Dfn` struct looks like this:

```rust
Dfn {
    lts: [Lt::Default, Lt::Arg(0)],
    tys: [Type::Array(Box::new(Type::Object)), Type::Object],
    ret: Type::Void
}
```

`Lt::Arg(0)` means the argument outlives the first argument.

Lifetimes must not be cyclic.
For example, this is not valid Dyon code:

```rust
fn foo(a: 'b, b: 'a) { ... }
```

`Lt::Return` means the arugment outlives the return value:

```rust
fn foo(a: 'return) -> { ... }
```
