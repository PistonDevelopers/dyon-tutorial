# Variables

```rust
a := 3 // Create a variable "a" with value `3`.
a = 4 // Change the value of variable "a" to `4`.
```

A variable has a name, a type and a value.

- The operator `:=` creates a variable.
- The operator `=` changes the value of a variable.

When changing the value of a variable, the type must be the same:

```rust
a := 3
a = "hi!" // ERROR
```

```
--- ERROR ---
main (source/test.dyon)

Expected assigning to text
3,5:     a = "hi!" // ERROR
3,5:     ^
```

### Echo example

Source code: [examples/echo](https://github.com/PistonDevelopers/dyon-tutorial/tree/master/examples/echo)

Create a new project and name it "echo".

Put this in "src/main.dyon":

```rust
fn main() {
    print("Type something: ")
    line := read_line()
    sleep(1)
    println(line)
}
```

This program prints out the text you gave it after 1 second.
The text is stored inside a variable "line".

### Comments

You might have noticed:

- `println` ends with a new line, while `print` stays at same line

Some things you can try:

1. Print out "You said: (line)"!
2. Change `sleep(1)` to wait 5 seconds!
3. Change the name of "line" to something else!
4. Put "println(line)" first and see what happens!
