# Objects

An object stores a list of values, organized as a dictionary. The type is `{}`.

```rust
a := {x: 1, y: "hi"}
```

To change a value in an object:

```rust
a.x = 2
```

Alternative:

```rust
a["x"] = 2
```

The value must be of the same type.

If you want to change the type, use `:=`:

```rust
a.x := "hi!"
```

Insert new keys and values with `:=`:

```rust
a := {}
a.x := 1
a.y := 2
a.z := 3
```

### Some useful functions

- `fn has({}, str) -> bool` - return `true` if object has key
- `fn keys({}) -> [str]` - return keys of object
