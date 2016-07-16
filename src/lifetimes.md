# Lifetimes

In Dyon, a lifetime tells whether an argument outlives another argument.

### Lifetimes are rare

In normal programming there is little need to worry about lifetimes.

For example, use `clone` when putting a variable inside another:

```rust
fn put(a, mut b) {
    b[0] = clone(a)
}
```

Instead of:

```rust
fn put(a: 'b, mut b) {
    b[0] = a
}
```

It is useful to know how lifetimes work, but you rarely need them in practice.

### Lifetimes replaces garbage collector

Some languages can have a pointer to a variable that does not exist.
When this happens, it is called "dangling pointer".
This can lead to unpredictable behavior and system crashes.
Languages that allow dangling pointer are unsafe,
and the programmer must be extra careful.

Many languages use a garbage collector to avoid dangling pointers.
Instead of removing the variable that the pointer points to,
it keeps it around in memory until all its pointers are gone.

Dyon uses static lifetime checks to ensure that dangling pointers are impossible.
This removes the need for a garbage collector.

### Lifetimes tell the order of declaration

A lifetime tells whether an argument outlives another argument:

```rust
// `a` outlives `b`
fn put(a: 'b, mut b) {
    b[0] = a
}

fn main() {
    a := [2, 3]     // - lifetime of `a`
                    // |
    b := [[]]       // |  - lifetime of `b`
                    // |  |
    put(a, mut b)   // |  |
}
```

The variable "a" outlives "b" because it is declared before "b".

The same program can be written like this:

```rust
fn main() {
    a := [2, 3]
    b := [[]]
    b[0] = a
}
```

Here, the order of the declared variables is known.

### The `return` lifetime

The `return` lifetime is the lifetime of the `return` variable.
This outlives the default lifetime of arguments (no lifetime).

If you return one of the argument, you must use `'return` or `clone`:

```rust
// With `'return` lifetime.
id(x: 'return) = x

// With `clone`.
id(x) = clone(x)
```

### The lifetime checker does not understand types

In Dyon, the static type is not guaranteed at runtime,
therefore `bool`, `f64` and `str` follows same rules as `[]` or `{}`:

```rust
fn foo(a: f64) -> {
    return a //
}
```

```
--- ERROR ---
In `source/test.dyon`:

Requires `a: 'return`
2,12:     return a //
2,12:            ^
```

### Lifetimes are about references

A lifetime is about the references stored inside a variable.
All references outlive variables are store in.
Variables can not store references to themselves,
because it can not outlive itself.

In order to put a reference inside a variable, the lifetime checker
must know that the reference outlives the variable.

Because of the lifetime checker, all memory in Dyon is an acyclic graph.
