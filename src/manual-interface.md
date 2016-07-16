# Manual interface

A manual interface gives more control over the interface between Rust and Dyon.
This is the only way to write external functions that mutate arguments.

The signature of an external function:

```rust
fn(rt: &mut Runtime) -> Result<(), String>
```

These functions are useful when pushing and popping variables:

- `Runtime::pop` - convert from stack
- `Runtime::pop_vec4` - convert 4D vector from stack
- `Runtime::var` - convert from variable
- `Runtime::var_vec4` - convert 4D vector from variable
- `Runtime::push` - convert to variable on stack
- `Runtime::push_vec4` - convert to 4D vector on stack
- `Runtime::resolve` - resolve a variable reference

### Getting arguments of function

Since the Dyon runtime uses a stack, you must pop the argument in reverse order.
Before you use an argument, you must use `Runtime::resolve` in case
it is a reference to a variable:

```rust
let draw_list = rt.stack.pop().expect("There is no value on the stack");
let arr = rt.resolve(&draw_list);
```

`Runtime::pop`, `Runtime::pop_var`, `Runtime::var` and `Runtime::var_vec4`
resolves the variable for you.

### Mutate argument

To mutate an argument, you need to obtain a mutable reference to the
resolved variable on the stack:

```rust
let v = rt.stack.pop().expect(TINVOTS);

if let Variable::Ref(ind) = v {
    let ok = if let Variable::Array(ref mut arr) = rt.stack[ind] {
        Arc::make_mut(arr)...;
    }
}
```

### Return value

After popping argument and computing a value, push the result on the stack.
Do not push more than one value, since Dyon only supports a single return value.

### Reading from a Dyon variable

The `Runtime::var` function converts a value inside a variable:

```rust
let radius: f64 = try!(rt.var(&it[2]));
```

### 4D vectors

The `Runtime::var_vec4` function converts to a `vec4` convertible type:

```rust
let color: [f32; 4] = try!(rt.var_vec4(&it[1]));
```

### Piston-Current

Dyon keeps no track of variables in the Rust environment.
You can use the [Piston-Current](https://github.com/pistondevelopers/current) crate to read from or change such variables by type.

```rust
pub fn render(rt: &mut Runtime) -> Result<(), String> {
    rt.push(unsafe { Current::<Option<Event>>::new()
        .as_ref().expect(NO_EVENT).render_args().is_some() });
    Ok(())
}
```
