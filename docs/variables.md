# Variables

## Val & Var

There are two types of variables: `val` and `var`. The latter is mutable and
thus can be changes after assigning a value. The type of a variable will
normally be inferred from the right hand expression but can be defined manually
too.

### EBNF Notation

```ebnf
variable = "var" | "val" , ( [ ":", name ] , "=" , expression | ":", name, [ "=" , expression ] ) ;
name = "a".."z" | "A".."Z", { "a".."z" | "A".."Z" | "0".."9" } ;
```

### Simple Notation

- `val foo`
- `var foo`
- `val: String foo`
- `var: String foo`
- `val foo = [expression]` *

<sub>See [expression](expressions.md) for details about expressions.</sub>
