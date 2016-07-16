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
