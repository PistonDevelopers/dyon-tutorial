# If

In Dyon, the `if` keyword runs a block if its condition is true:

```rust
a := 3 < 4
if a {
    println("hi!")
}
```

An `else` block runs when previous conditions are false:

```rust
a := 3 > 4
if a {
    println("yes!")
} else {
    println("no...")
}
```

An `else if` block runs when previous conditions are false and its condition is true:

```rust
a := 2
if a == 0 {
    println("=0")
} else if a == 1 {
    println("=1")
} else if a == 2 {
    println("=2")
} else {
    println(">2")
}
```

An `if` can be used as an expression:

```rust
a := 3
b := 3
c := 2 + if a == b { 1 } else { 0 }
```
