# 4D vectors

In Dyon, you can compute with 4D vectors:

```
(x, y, z, w)
```

Many operations are built-in for working with 4D vectors:

```rust
a := (1, 2, 3, 4)
b := (5, 6, 7, 8)
println(a + b) // prints `(6, 8, 10, 12)`
```

The components `z` and `w` are set to 0 by default:

```rust
a := (1, 2)
```

The `y` component can also be set to 0, but requires ",":

```rust
a := (1,)
```

### HTML hex colors

A HTML hex color is converted into a 4D vector:

```
a := #ff0000 // red
b := #00ff00 // green
c := #0000ff // blue
d := #00000033 // semi-transparent black
```

### Swizzle components

To swizzle components, you can use this notation:

```rust
a := (1, 2)
b := (yx a,)
```

You can repeat a component up to 4 times:

```rust
a := (1, 2)
b := (yyyy a,)
println(b) // prints `(2, 2, 2, 2)`
```

### Calling functions

When calling a function, you can unpack vector components:

```rust
add(x, y) = x + y

fn main() {
    a := (1, 2)
    println(add(xy a)) // prints `3`
}
```

If a function takes named arguments, you can use this trick:

```rust
add__x_y(x, y) = x + y

fn main() {
    a := (1, 2)
    println(add(x_y: xy a)) // prints `3`
}
```

### Addition and multiplication

Addition and multiplication is per component for two vectors.

```rust
(1, 2) + (3, 4) // `(4, 6)`
(1, 2) * (3, 4) // `(3, 8)`
```

Scalar addition, multiplication and division is allowed on both sides
and is per component.

```rust
(1, 2) + 1 // `(2, 3, 1, 1)`
3 + (1, 2) // `(4, 5, 3, 3)`
(1, 2) * 2 // `(2, 4)`
2 * (1, 2) // `(2, 4)`
(1, 2) / 2 // `(0.5, 1)`
2 / (1, 2, 4, 8) // `(2, 1, 0.5, 0.25)`
```

### Dot product

Dot product of two vectors can be written in two ways:

```rust
a := (1, 2)
b := (3, 4)
println(a *. b)
println(a · b)
```

### Cross product

Cross product of two vectors can be written in two ways:

```rust
a := (1, 2)
b := (3, 4)
println(a x b)
println(a ⨯ b)
```

### Norm

The norm of a vector, also called "length" or "magnitude":

```rust
a := (3, 4)
println(|a|)
```

### Un-loops

The `vec4`, `vec3`, `vec2` are un-rolled and replaces the index with a number:

```rust
fn main() {
    a := vec4 i { i + 1 }
    println(a) // prints `(1, 2, 3, 4)`
}
```

You can check this by printing out a closure:

```rust
fn main() {
    a := \() = vec4 i { i + 1 }
    // prints `\() = ({ 0 + 1 }, { 1 + 1 }, { 2 + 1 }, { 3 + 1 })`
    println(a)
}
```

### Other functions for 4D vectors:

- `fn x(vec4) -> f64` - get x component
- `fn y(vec4) -> f64` - get y component
- `fn z(vec4) -> f64` - get z component
- `fn w(vec4) -> f64` - get w component
- `fn s(vec4, f64) -> f64` - get vector component by index
- `fn dir__angle(f64) -> vec4` - rotation vector around Z axis

### Precision

Whenever you do calculations with 4D vectors, you get float 32 bit precision.
