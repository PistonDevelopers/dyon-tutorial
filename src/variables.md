# Variables

The name "variable" means something that can change.
Variables store data inside a program.

Create a new project "echo", or edit the "hello_world" project.

In "src/main.dyon", type the following:

```dyon
fn main() {
    print("Type something: ")
    line := read_line()
    sleep(1)
    println(line)
}
```

The operator `:=` is used to create a variable.

A variable has a name, a type and a value.
The name is "line", and the value is the result of `read_line()`.

The code `read_line()` returns only variables of type `str`.
This becomes the type of the variable with name "line".

### Changing value of variables

The value of a variable can be changed with the `=` operator:

```dyon
a := 3
a = 4
```

The new value must be of same type as the variable.

```dyon
a := 3
a = "hi!" // ERROR
```

### Comments

A few things you might have noticed:

- Dyon runs the program from top to bottom
- When it has finished one line, it goes to the next one
- The program stops when the last line in "main" is finished
- To use a variable, you must type the exact name

Some things you can try:

1. Print out "You said: (line)"!
2. Change `sleep(1)` to wait 5 seconds!
3. Change the name of "line" to something else!
4. Put "println(line)" first and see what happens!
