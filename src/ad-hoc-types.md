# Ad-hoc types

In Dyon, an ad-hoc type is a type that you just give a name:

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
