# Infer range

In Dyon, the range of a mathematical loop can be inferred from the loop body.

You can leave out the start and end if you use an index on a list:

```rust
list := [1, 2, 3]

for i {
    println(list[i])
}
```

This is equivalent to:

```rust
list := [1, 2, 3]

for i len(list) {
    println(list[i])
}
```

For nested loops, the indices must follow the same order as the loops:

```rust
list := [[[1, 2], [3, 4]], [[5, 6], [7, 8]]]
for i {
    for j {
        for k {
            println(list[i][j][k])
        }
    }
}
```
