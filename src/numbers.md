# Numbers

A number in Dyon is a variable that stores floats with 64 bit precision.
The type is `f64`.

```rust
a := 1
b := .5
c := 2.5
d := -3
e := 1_000_000
f := 1e6
g := -7_034.52e-22
```

You can add, subtract, multiply, divide, take the power and find the division reminder:

```rust
a := 2
b := a + 3
c := a - 3
d := a * 3
e := a^3
f := a / 3
g := a % 3
```

### Relative change

The following operators change the value relatively:

```rust
a += 1 // increase by 1
a -= 1 // declare by 1
a *= 2 // multiply by 2
a /= 2 // divide by 2
a %= 2 // find division reminder of 2
```

### Comments

Some thing you might have noticed:

- `f64` is used by both Rust and Dyon
- "One million" can be written as `1_000_000` or `1e6`
