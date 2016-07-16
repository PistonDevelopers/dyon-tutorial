# Closures

A closure in Dyon is a variable that works similar to a mathematical function.

```rust
a := \(x) = x + 1
```

You can print out a closure:

```rust
// prints `\(x: any) = x + 1`
println(\(x) = x + 1)
```

To call a closure, use the `\` character before the name:

```rust
a := \(x) = x + 1
println(\a(0)) // prints `1`
```

### Calling closures on objects

When an object stores a closure, you can call it with named arguments:

```rust
fn main() {
    gollum := {say__msg: \(msg) = "My precious " + msg}
    // prints `my precious ring`
    println(\gollum.say(msg: "ring"))
}
```


### Grab

Use `grab` to compute a value and insert it into a closure:

```rust
a := 2
b := \(x) = (grab a + 2) + x
// prints `\(x: any) = 4 + x`
println(b)
```

When a closure is inside another closure, you can use `grab '2`:

```rust
a := 2
b := \(x) = \(y) = (grab '2 a) + (grab x) + y
// prints `\(x: any) = \(y: any) = 2 + (grab x) + y`
println(b)
// prints `\(y: any) = 2 + 0 + y`
println(\b(0))
```

You can use `grab 'N` where `N` is the level you want to compute from.
