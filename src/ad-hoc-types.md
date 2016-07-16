# Ad-hoc types

In Dyon, an ad-hoc type is a type that you just give a name.
It is not declared anywhere, but used directly when writing the functions.
Dyon treats ad-hoc types as distinct from each other.

```rust
fn new_person(first_name: str, last_name: str) -> Person {
    return {
        first_name: clone(first_name),
        last_name: clone(last_name)
    }
}

fn say_hello(person: Person) {
    println("Hi " + person.first_name + "!")
}

fn main() {
    homer := new_person("Homer", "Simpson")
    say_hello(homer) // prints `Hi Homer!`
}
```

You can use any name that is not used by other Dyon types.
It is common to use CamelCase.

`Person` is the same as `Person {}`, where `{}` is the inner type.

The inner type goes with the ad-hoc type and vice versa:

```rust
fn say_hello(person: Person) {
    println("Hi " + person.first_name + "!")
}

fn main() {
    say_hello({first_name: "Homer"}) // prints `Hi Homer!`
}
```

### Addition and multiplication

Two ad-hoc types can be added if the inner type allows addition.

Dyon complains if you try to add an ad-hoc type with an inner type.

For example:

```rust
// Convert number to `km`
fn km(v: f64) -> km f64 { return v }

km(3) + km(4) // OK
km(3) + 4 // ERROR
```

Multiplication is not allowed, because this often changes physical units.
