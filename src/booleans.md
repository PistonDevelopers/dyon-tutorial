# Booleans

A boolean in Dyon is a variable that stores `true` or `false`.
This represents a choice with two options.
The type is `bool`.

### Lazy and eager

A lazy operator does not compute the right argument if the left argument gives the result.

An eager operator computes both arguments.

### Logical gates

A logical gate is an operation on two boolean values.

A      |B      |A AND B|A OR B|A XOR B|A EXC B
-------|-------|-------|------|-------|-------
false  |false  |false  |false |false  |false
false  |true   |false  |true  |true   |false
true   |false  |false  |true  |true   |true
true   |true   |true   |true  |false  |false

There are 4 operators for AND:

```dyon
a && b // lazy
a and b // eager
a ∧ b // eager
a * b // eager
```

There are 4 operators for OR:

```dyon
a || b // lazy
a or b // eager
a ∨ b // eager
a + b // eager
```

There is 1 operator for XOR:

```dyon
a ^ b
```

There is 1 operator for EXC:

```dyon
a - b
```

There are 2 operators for NOT:

```dyon
!a
¬a
```

### Why more than one way

Boolean algebra is used with different notations:

- Programming applications
- Logic
- Non-invertible sets

When programming applications, you use `&&`, `||` and `!`.

Logic use `∧`, `∨` and `¬`.

Non-invertible sets use `*`, `+` and `-`.

In the future Dyon might get more features for Boolean algebra.
