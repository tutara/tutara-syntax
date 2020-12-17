# Modules

::: warning
Modules are still an early concept feature and are subject to change.
:::

Importing and exporting code works using modules. To define a file to be a
module you specify the this in the file itself using the `mod` keyword.

A module can only contain classes and functions in the top-level. Other code is
not allowed within a module and should be added inside functions or classes.

All members are exported since there is no concept of visibility in the language.

```ttr{1-2}
// Set the module name for this file
mod math

fun: Int add(a: Int, b: Int) {
  return a + b
}

fun: Int subtract(a: Int, b: Int) {
  return a - b
}
```

Using functions or classes from a module is done using the `use` keyword.

```ttr{1-2}
// Use the "add" function from the "math" module
use math.add

val foo = add(12, 30)
```

When using multiple members from the same module it's also possible to use a
special syntax using curly brackets. This way multiple members can be used with
a single statement.

```ttr{1-2}
// Use the "add" and "subtract" functions from the "math" module
use math.{add, subtract}

val foo = add(12, 30)
val bar = subtract(100, 58)
```
