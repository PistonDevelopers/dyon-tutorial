# Arrays

An array stores a list of values. The type is `[]`.

```rust
a := [1, 2, 3]
```

You can store values of different types in the same array:

```rust
a := [1, "hi", [1, 2, 3]]
```

To access an value inside an array, you use a number that start at `0`:

```rust
a := [1, 2, 3]
println(a[0]) // prints `1`
println(a[1]) // prints `2`
println(a[2]) // prints `3`
```

### Multi-dimensional arrays

An array can contain arrays.
This makes it possible to represent grids in 2D, 3D etc.

```rust
a := [1, 2, 3] // 1D
println(a[0]) // prints `1`

b :=  [ // 2D
          [1, 2, 3],
          [4, 5, 6],
          [7, 8, 9],
      ]
println(b[0][0]) // prints `1`

c :=  [ // 3D
          [[1, 2], [3, 4]],
          [[5, 6], [7, 8]],
      ]
println(a[0][0][0]) // prints `1`
```

### Memory

Each item in an array takes 24 bytes (64 bit platforms):

- 8 bytes for type information
- 16 bytes for item data

This is optimized to store 4D vectors.
