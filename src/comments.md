# Comments

A comment is text to explain how some code works.
Comments are ignored when running the program.

Dyon uses `//` for single-line and `/* */` for multi-line comments.

```dyon
/*

  this program was made by
==== SUPER INTELLIGENCE ====
from another space dimension

*/

fn main() {
    // Can I ask you something?
    println("hello?")
}
```

A single-line comment ignores the rest of the line:

```dyon
println("hello") // Prints `hello`.
```

A multi-line comment starts with `/*` and ends with `*/`.

```dyon
println(/* testing, testing! */ "hello")
```

You can nest `/* */`:

```dyon
/*
    /*
    A comment inside a comment!
    */
*/
```

### Tips and tricks

It is more common to use `//` than `/* */` for documenting the code.

End a comment with a dot to make it easier to read:

```dyon
// Alice opened the door
// by pressing a button.
```

You can use `/* */` to ignore some code without removing it.
This is useful when you try out different programs:

```dyon
/*
fn main() {
    println("one")
}
*/

fn main() {
    println("two")
}
```

Organize the code in paragraphs, just like in a book.
Write a single-line comment for each paragraph.
Separate paragraphs with an empty line:

```dyon
fn main() {
    // Print the numbers from 1 to 10.
    list := sift i 10 { i + 1 }
    println(list)

    // Print the numbers from 11 to 20.
    list := sift i [10, 20) { i + 1 }
    println(list)
}
```
