# 4D vectors

In Dyon, you can compute with 4D matrices:

```
mat4 {
  m00, m01, m02, m03;
  m10, m11, m12, m13;
  m20, m21, m22, m23;
  m30, m31, m32, m33;
}
```

Many operations are built-in for working with 4D matrices:

```
fn main() {
    a := mat4 {1,;}
    b := mat4 {1,;}
    // prints `mat4 {2,0,0,0; 0,2,0,0; 0,0,2,0; 0,0,0,2}`
    println(a + b)
}
```

4D vectors used as rows:

```
mat4 {(1, 0, 0, 0); (0, 1, 0, 0); (0, 0, 1, 0); (0, 0, 0, 1)}
```

Omitted parentheses:

```
mat4 {1,0,0,0; 0,1,0,0; 0,0,1,0; 0,0,0,1}
```

Omitted trailing zeroes:

```
mat4 {1,; 0,1; 0,0,1; 0,0,0,1}
```

Fills out rows corresponding to identity matrix:

```
mat4 {1,; 0,1; 0,0,1}
```

Identity matrix:

```
mat4 {1,;}
```

### Addition and multiplication

Addition is per component for two matrices.

Multiplication is matrix multiplication.

```
fn main() {
    a := mat4 {1,;}
    b := a + a
    // Prints `mat4 {2,0,0,0; 0,2,0,0; 0,0,2,0; 0,0,0,2}`.
    println(b)

    // Prints `mat4 {4,0,0,0; 0,4,0,0; 0,0,4,0; 0,0,0,4}`.
    c := b * b
    println(c)
}
```

`+=`, `-=` and `*=`:

```
fn main() {
    a := mat4 {1,;}
    a += a
    // Prints `mat4 {2,0,0,0; 0,2,0,0; 0,0,2,0; 0,0,0,2}`.
    println(a)

    // Prints `mat4 {4,0,0,0; 0,4,0,0; 0,0,4,0; 0,0,0,4}`.
    a *= a
    println(a)

    // Prints `mat4 {3,0,0,0; 0,3,0,0; 0,0,3,0; 0,0,0,3}`
    a -= mat4 {1,;}
    println(a)
}
```

`+`, `-` and `*` with scalars and matrices is per component:

```
fn main() {
    a := mat4 {1,2,3,4;2,3,4,1;3,4,1,2;4,1,2,3}
    println(2 * a)
    println(a * 2)
    println(2 + a)
    println(a + 2)
    println(2 - a)
    println(a - 2)
}
```

Transform 4D vector by multiplying a 4D matrix with a `vec4` that has a zero in the 4th component:

```
fn main() {
    // Scale x-axis up 2 times.
    a := mat4 {2,;}
    println(a * (1, 1, 1))

    // Scale y-axis up 2 times.
    a := mat4 {1,; 0,2}
    println(a * (1, 1, 1))

    // Scale z-axis up 2 times.
    a := mat4 {1,; 0,1; 0,0,2}
    println(a * (1, 1, 1))
    // The same using `scale`.
    println(scale((1, 1, 2)) * (1, 1, 1))
}
```

Transform a point by multiplying a 4D matrix with a `vec4` that has a one in the 4th component:

```
fn main() {
    pos := (1, 2, 3)
    // Put `1` in the 4th component to transform a point.
    println(mov((1, 2)) * (xyz pos, 1))
}
```

Get row vectors with `rx`, `ry`, `rz`, `rw`, `rv` and get column vectors with `cx`, `cy`, `cz`, `cw`, `cv`:

```
fn main() {
    a := mat4 {
        1,2,3,4;
        5,6,7,8;
        9,10,11,12;
        13,14,15,16;
    }

    // Print row vectors.
    println(rx(a)) // Prints `(1, 2, 3, 4)`.
    println(ry(a)) // Prints `(5, 6, 7, 8)`.
    println(rz(a)) // Prints `(9, 10, 11, 12)`.
    println(rw(a)) // Prints `(13, 14, 15, 16)`.

    // Print row vectors using a loop.
    for i 4 {println(rv(a, i))}

    // Print column vectors.
    println(cx(a)) // Prints `(1, 5, 9, 13)`
    println(cy(a)) // Prints `(2, 6, 10, 14)`
    println(cz(a)) // Prints `(3, 7, 11, 15)`
    println(cw(a)) // Prints `(4, 8, 12, 16)`

    // Print column vectors using a loop.
    for i 4 {println(cv(a, i))}
}
```

### Negation

Negation is per component:

```
a := mat4 {1,;}
// Prints `mat4 {-1,0,0,0; 0,-1,0,0; 0,0,-1,0; 0,0,0,-1}`
println(-a)
```

### Other functions for 4D vectors:

- `fn det(m: mat4) -> f64` determinant
- `fn inv(m: mat4) -> mat4 ` inverse
- `fn mov(v: vec4) -> mat4` translation
- `fn scale(v: vec4) -> mat4` scale
- `fn rot__axis_angle(axis: vec4, angle: f64) -> mat4` axis-angle rotation
- `n ortho__pos_right_up_forward(pos: vec4, right: vec4, up: vec4, forward: vec4) -> mat4` orthogonal view
- `fn proj__fov_near_far_ar(fov: f64, near: f64, far: f64, ar: f64) -> mat4` projection view
- `fn mvp__model_view_projection(model: mat4, view: mat4, projection: mat4) -> mat4` model-view-projection

### Precision

Whenever you do calculations with 4D matrices, you get float 32 bit precision.
