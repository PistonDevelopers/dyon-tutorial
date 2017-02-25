# Loops

In Dyon there are 4 kinds of loops:

- Infinite loop
- Traditional For loop
- Mathematical loops
- Link loop

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
- `∑vec4`/`sum_vec4` - add 4D vectors to get the sum
- `∏vec4`/`prod_vec4` - multiply 4D vectors to get the product

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

### Link loop

The link loop is similar to a link block, but for a repeated pattern.

```rust
list := [1, 2, 3]
println(link i {(i+1)": "list[i]})
```

All evaluated expressions are appended to the link.
Expressions that do not return a value are allowed inside a link loop.

Pro-tip: A link block inside a link loop gives you an all-or-nothing behavior.

```rust
ffn main() {
    people := [{name: "Homer"}, {name: "Bart"}, {name: "Marge"}]
    kids := link i {link {
        "name: "
        name := people[i].name
        if name == "Bart" {continue} else {name}
        "\n"
    }}
    print(kids)
}
```
