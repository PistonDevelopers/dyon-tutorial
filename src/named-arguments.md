# Named arguments

In Dyon, you can call some functions in two ways:

```rust
attack__player_enemy(mut player, enemy)
attack(player: mut player, enemy: enemy)
```

The named arguments are part of the function name.

- Double underscores separates function name from arguments
- Arguments are separated by a single underscore

It is common to use named arguments when there are lots of parameters.
