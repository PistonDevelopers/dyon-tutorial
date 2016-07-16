# Types

In Dyon, there are two kinds of types:

- Runtime types, which only has one level
- Static types, which can have more than one level

### Runtime types

Runtime types are checked with the `typeof` function:

```rust
fn main() {
    println(typeof(1.2)) // prints `number`
    println(typeof(true)) // prints `boolean`
    println(typeof("hi!")) // prints `string`
    println(typeof((1, 2))) // prints `vec4`
    println(typeof([1, 2, 3])) // prints `array`
    println(typeof({a: 2})) // prints `object`
    println(typeof(link { 1 2 3 })) // prints `link`
    println(typeof(some(2))) // prints `option`
    println(typeof(ok(2))) // prints `result`
    println(typeof(go foo())) // prints `thread`
    println(typeof(\(x) = x + 1)) // prints `closure`
    println(typeof(unwrap(load("src/main.dyon")))) // prints `rust_object`
}

fn foo() -> { return ok(2) }
```

### Static types

Function arguments can have specify a static type:

```rust
fn foo(a: f64) { ... }
```

By default this is `any`.

Static types are used by the type checker to check for errors:

- `any`, any type
- `f64`, number
- `bool`, boolean
- `str`, string
- `vec4`, 4D vector
- `[]`, array, defaults to `[any]`
- `{}`, object
- `link`, link
- `opt`, defaults to `opt[any]`
- `res`, defaults to `res[any]`
- `thr`, defaults to `thr[any]`
- Closure type, e.g. `\(any, ..) -> any`
- Ad-hoc type, e.g. `Foo`, defaults to `Foo {}`

There is no static type for Rust objects. Use an ad-hoc type, e.g. `Foo any`.
