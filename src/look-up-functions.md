# Look up functions

In Dyon, you get all available functions with `functions`:

```rust
fn main() {
    println(functions())
}
```

You can write a program that looks up the information about a function:

```rust
fn main() {
    fs := functions()
    has_foo := any i { fs[i].name == "foo" }
    if has_foo {
        why := why(has_foo)
        println(fs[why[0]])
    }
}

fn foo() {}
```

```
{returns: "void", type: "loaded", arguments: [], name: "foo"}
```

Because Dyon uses dynamic modules, `functions` is the only standard way
of obtaining this information. This can only be known in the loaded module.
