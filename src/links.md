# Links

A link in Dyon is a variable that stores `bool`, `f64` and `str` efficiently.
It is called "link" because it is fast and easy to put together data.

```rust
name := "John"
a := link {"Hi "name"!"}
```

The data inside a link can not be changed.
You can read the data using `head` and `tail`:

```rust
a := link { 1 2 3 }
b := head(a) // `some(1)`
c := tail(a) // `link { 2 3 }`
```

When you put a link inside a link, it gets flattened:

```rust
a := link { 1 2 3 }
// `link { "start "1 2 3" end" }`
b := link { "start "a" end" }
```

### When to use links

Links are often used to:

- Generate lots of data and then convert to `str`
- Pre-process parts of a text template
- Generate a web page
- Code generation
- Store lots of `f64`, `bool` or `str` in memory

Because of the easy syntax for links, you can use Dyon as a template language.

### Memory

The memory of a link is divided into blocks of 1024 bytes (64 bit platforms).

A link takes only 3.2% extra memory than the ideal amount when blocks are filled.

To save memory with a link compared to an array, you need 42 items:

```rust
a := link {
        0 1 2 3 4 5 6 7 8
        9 10 11 12 13 14 15 16
        17 18 19 20 21 22 23 24
        25 26 27 28 29 30 31 32
        33 34 35 36 37 38 39 40
        41 42
    }
```

### Other operators

You can use `+=` (back) and `-=` (front) to link together link blocks.
This is faster, but uses a little more memory.

You can not use `+` because it is too easy to waste memory by error.
