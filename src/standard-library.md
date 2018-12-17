# Standard Library

Dyon organizes functions in 3 ways:

1. Dyon modules (also called "loaded functions")
2. Rust interop (also called "external functions")
3. Standard Library (also called "intrinsics")

1) and 2) are explained in previous chapters.

This chapter is about the third point 3) Standard Library.

This is what the Standard Library contains:

- Functions for loading modules and calling functions
- Functions for using Dyon's built-in types
- Functions for loading and saving data
- Functions for meta-parsing

The standard library of Dyon is small compared to e.g. Rust (less than 150 functions).
If you want to know the details of how it works, you can read the source code [here](https://github.com/PistonDevelopers/dyon/tree/master/src/dyon_std).

Some functions are in the standard library because they use
special knowledge that is not available in external functions.

This chapter shows some things you can do with the Standard Library.
