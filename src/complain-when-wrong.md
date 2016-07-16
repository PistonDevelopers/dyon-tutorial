# Complain when wrong

In Dyon, the type checker only complains when it knows something is wrong.

When you do not specify the type of an argument, it defaults to `any`:

```rust
foo(x) = x + 1

fn main() {
    println(foo(false))
}
```

In the program above, the type checker does not know that something is wrong.

You get a runtime error:

```
--- ERROR ---
main (source/test.dyon)
foo (source/test.dyon)

Invalid type for binary operator `"+"`, expected numbers, vec4s, bools or strings
1,10: foo(x) = x + 1
1,10:          ^
```

To get a type error, add the type to the argument:

```rust
foo(x: f64) = x + 1
```

Now the type checker complains, because it knows that `false` is not `f64`:

```
--- ERROR ---
In `source/test.dyon`:

Type mismatch (#100):
Expected `f64`, found `bool`
4,17:     println(foo(false))
4,17:                 ^
```

### Static types are not guaranteed

The type of an argument is not guaranteed to be the given static type.

For example:

```rust
foo(x: f64) = x + 1

forget_type(x: any) = clone(x)

fn main() {
    println(foo(forget_type(false))) // ERROR
}
```

This gives you a runtime error, because the type checker is not that smart.
