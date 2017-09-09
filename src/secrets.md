# Secrets

In Dyon, a secret is a hidden array of values associated with a `bool` or `f64`.
The type is `sec[bool]` or `sec[f64]`.

Secrets are used in combination with `any`/`all`/`max`/`min` loops.
This feature helps developers to write short and correct code.

For example, you can use secrets to find the first item in a list that
satisfies a condition:

```rust
list := [1, 2, 3]
a := any i { list[i] > 2 }
if a {
    println(why(a)) // prints `[2]` because `list[2] == 3` and `3 > 2`.
}
```

It also works for lists inside lists:

```rust
list := [[1, 2], [3, 4]]
a := any i, j { list[i][j] > 2 }
if a {
    println(why(a)) // prints `[1, 0]` because `list[1][0] == 3` and `3 > 2`.
}
```

`max` and `min` loops uses the `where` keyword to unlock the secret:

```rust
list := [1, 2, 3, 4]
a := max i { list[i] }
println(where(a)) // prints `[3]` because `list[3]` is the greatest number.
```

Secrets are used to solve problems that otherwise would be a bit tricky to code.
For example, the "minimax" algorithm which is
used to pick the best move when playing a zero-sum game:

```rust
payoff := [[0, 1], [2, -1]]
a := min i {max j { payoff[i][j] }}
println(where(a)) // prints `[0, 1]` because that is the best move.
```

In the beginning secrets might feel a bit "backwards".
Instead of reducing a query into a `bool`, one can extract information from them!
Do not worry, because you will get used to it and you will like this feature
when programming complex logic.

Use `explain_why` to add a secret to a `bool`:

```rust
a := explain_why(true, "hi!")
if a {
    println(why(a)) // prints `["hi!"]`
}
```

Use `explain_where` to add a secret to a `f64`:

```rust
a := explain_where(2.5, "giant")
println(where(a)) // prints `["giant"]`
```

A secret propagates from the left argument of a binary operator:

```rust
a := explain_where(2.5, "giant")
is_tall := a > 2.0
if is_tall {
    println(why(is_tall)) // prints `["giant"]`
}
```

When using a `min`, `max`, `any` or `all`, the indices are automatically added as secrets:

```rust
list := [[1, 2], [3, 4]]
println(why(any i, j { list[i][j] > 2 })) // prints `[1, 0]`
```

### A secret must have meaning

The function `why` will only work if the value is `true`.
This prevents programs that do not make sense, such as:

```rust
list := [1, 2, 3]
println(why(all i { list[i] < 10 }))
```

```
--- ERROR ---
main (source/test.dyon)
why

This does not make sense, perhaps an array is empty?
3,17:     println(why(all i { list[i] < 10 }))
3,17:                 ^
```

Likewise, `where` will only work if the value is not `NaN` (0/0):

```rust
list := []
println(where(min i { list[i] }))
```

```
--- ERROR ---
main (source/test.dyon)

This does not make sense, perhaps an array is empty?
3,19:     println(where(min i { list[i] }))
3,19:                   ^
```

Remember to check for empty arrays!

### Overhead

Since Dyon supports 4D vectors, the size of the `Variable` enum is quite large.
This means better performance for 4D vectors but slower performance for `bool` and `f64`.
Dyon is designed for game development so this is a reasonable trade-off.
The overhead from executing extra instructions for secrets is not that large because of good cache locality.
