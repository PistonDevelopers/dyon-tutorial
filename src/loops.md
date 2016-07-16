# Loops

In Dyon there are 3 kinds of loops:

- Infinite loop
- Traditional For loop
- Mathematical loops

### Infinite loop

```rust
loop {
    println("hi!")
    sleep(1)
}
```

An infinite loop runs runs forever, or until `break` is used inside it.

Tip: Use Ctrl+C to terminate an infinite loop in the Terminal window.

### Traditional For loop

```rust
for i := 0; i < 10; i += 1 {
    println(i)
}
```

A traditional loop is similar to the loop in the programming language C.
It takes 3 expressions:

- Initialize, called first and once, e.g. `i := 0`
- Condition, checked for each turn, e.g. `i < 10`
- Step, called after each turn, e.g. `i += 1`

### Mathematical loops

Dyon is famous for its mathematical loops:

- `for` - do something for each turn
- `sift` - create an array out of values
- `min` - find the minimum value
- `max` - find the maximum value
- `∃`/`any` - check whether a condition is true for any value
- `∀`/`all` - check whether a condition is true for all values
- `∑`/`sum` - add values to get the sum
- `∏`/`prod` - multiply values to get the product

In mathematics, it is very common to loop over an index.
An index starts at 0, and increases with 1 for each turn.
All mathematical loops uses the same index notation.

```rust
for i 10 {
    println(i)
}
```

This is equivalent to `for i := 0; i < 10; i += 1`.

You can also specify the start and end value:

```rust
for i [0, 10) {
    println(i)
}
```
