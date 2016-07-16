# Packed loops

In Dyon, you can pack mathematical loops together of the same kind:

```rust
for i, j, k {
    println(list[i][j][k])
}
```

This is equivalent to:

```rust
for i {
    for j {
        for k {
            println(list[i][j][k])
        }
    }
}
```

You can also specify start and end for each index:

```rust
fn main() {
    list := [1, 2, 3, 4]
    n := len(list)

    // For each pair.
    for i n, j [i + 1, n) {
        println(abs(list[i] - list[j]))
    }
}
```

Pro tip: If you find a packed loop hard to understand,
you can print out closure to see how it works:

```rust
fn main() {
    a := \() = {
        list := [[[1, 2], [3, 4]], [[5, 6], [7, 8]]]
        for i, j, k {
            println(list[i][j][k])
        }
    }
    println(a)
}
```
