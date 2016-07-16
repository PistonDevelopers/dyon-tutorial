# Comments

A comment is text to explain how some code works.
Comments are ignored when running the program.

Dyon uses `//` for single-line and `/* */` for multi-line comments.

```rust
/*

This text is inside a multi-line comment.
It is ignored when running the program.

*/

fn main() {
    // Can I ask you something?
    println("hello?")
}
```

A single-line comment ignores the rest of the line:

```rust
println("hello") // Prints `hello`.
```

A multi-line comment starts with `/*` and ends with `*/`.

```rust
/* testing, testing! */
println("hello")
```

You can nest `/* */`:

```rust
/*
    /*
    A comment inside a comment!
    */
*/
```

### Tips and tricks

It is more common to use `//` than `/* */` for documenting the code.

End a comment with a dot to make it easier to see where the line is ending:

```rust
// Alice opened the door
// by pressing a button.
```

You can use `/* */` to ignore some code without removing it:

```rust
/*
fn main() {
    println("one")
}
*/

fn main() {
    println("two")
}
```

One technique that helps making code more understandable:
Organize the code in paragraphs, like in a book.
Write a single-line comment for each paragraph.
Separate paragraphs with an empty line.

```rust
fn main() {
    // Print the numbers from 1 to 10.
    list := sift i 10 { i + 1 }
    println(list)

    // Print the numbers from 11 to 20.
    list := sift i [10, 20) { i + 1 }
    println(list)
}
```
