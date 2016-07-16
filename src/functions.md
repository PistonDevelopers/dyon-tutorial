# Functions

In Dyon, there are two ways to declare a function.

One way is to use `fn` to define a function:

```rust
fn f(x) -> {
    return x + 1
}
```

If a function does not return a value, you leave out `->`:

```rust
fn say_hi() {
    println("hi!")
}
```

Another way is to use mathematical notation:

```rust
f(x) = x + 1
```

All mathematically declared functions returns a value.

Pro tip: To declare constants, use mathematical notation:

```rust
// Speed of light.
c() = 299_792_458
```

### Fibonacci example

Source code: examples/fibonacci

```rust
fib(x) = if x <= 0 { 0 }
         else if x == 1 { 1 }
         else { fib(x-1) + fib(x-2) }

fn main() {
    for i 20 { println(fib(i)) }
}
```

Do not worry if you do not understand the code above.
This is just to show how to declare a function and call it.
