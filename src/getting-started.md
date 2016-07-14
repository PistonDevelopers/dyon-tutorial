# Getting started

Dyon is written in the Rust programming language.
You do not need to know Rust to use Dyon.
These two languages are like yin and yang.
They are very different in some ways, but complement each other.

Before you can run Dyon programs, you need to do the following:

1. Install [Rust](https://www.rust-lang.org/en-US/).
2. Open up the Terminal window
3. Type `cargo new --bin hello_world`

Open up Cargo.toml and add the following:

```
[dependencies]
dyon = 0.8.0
```

To start a Dyon program we need to write a little Rust.

Open up "src/main.rs" and type:

```rust
extern crate dyon;

use dyon::{error, run};

fn main() {
    error(run("src/main.dyon"));
}
```

Create a new file "src/main.dyon" and write:

```dyon
fn main() {
    println("Hello world!")
}
```

In the terminal window, go to the "hello_world" folder and type:

```
$ cargo run
```

This should print out:

```
Hello world!
```

### Comments

A few things you might have noticed:

- Dyon has no ";" at the end of lines
- The "fn" keyword is used by both Rust and Dyon
- The "main" function is called when running the program
- Double quotes "" are used for text

Some things you can try:

1. Put your name inside the text!
2. Add a new line where you print out something else!
3. Change "println" to "print" and see what happens!
