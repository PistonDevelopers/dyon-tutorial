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
