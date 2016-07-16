# Strings

A string in Dyon is a variable that stores UTF-8 bytes.
This represent text.
The type is `str`.

Use double quotes to write a string:

```rust
a := "hi!"
```

The `\` symbol escapes special characters:

- `\n` - New line
- `\t` - Tab
- `\"` - The `"` character
- `\\` - The `\` character
- `\r` - Moves to beginning of line without creating a new line
- `\u005c` - Unicode character by 4 hexadecimal code

The `+` operator joins two strings together:

```rust
name := "Santa"
title := "hi " + name
```

The `str` function converts a value into a string:

```rust
age := 58
println("Bilbo is " + str(age) + " years old!")
```

### Some useful functions for strings

- `fn str(any) -> str` - convert a variable to a string
- `fn read_line() -> str` - read line from standard input
- `fn trim(str) -> str` - trims away whitespace at both sides
- `fn trim_left(str) -> str` - trims away whitespace at left side
- `fn trim_right(str) -> str` - trims away whitespace at right side
- `fn json_string(str) -> str` - creates a JSON string
- `fn str__color(vec4) -> str` - HTML hex color string
- `fn chars(str) -> [str]` - characters of a string
