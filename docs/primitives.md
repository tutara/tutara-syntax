# Primitives

Primitives are fundamental types like booleans, integers and strings.

## Booleans

A boolean can either be `true` or `false`. It is comparable to a yes/no or
on/off state.

### EBNF Notation

```ebnf
boolean = "true" | "false" ;
```

### Example

```ttr
true
false
```

## Integers

Integers can be any valid whole number. They can not start with the digit `0`.

### EBNF Notation

```ebnf
integer = "0" | [ "-" ] , "1".."9" , { "0".."9" } ;
```

### Example

```ttr
0
-54
13
```

## Strings

A string is a sequence of characters. Strings are the basic of any text in the
language. Strings are enclosed between single quotation marks `'`. To use
variables inside of string you'll have to use the dollar sign, `$` ,follow by
variable castable to string. When using methods or accessing properties on an
object the expression must be enclosed between curly brackets `${}`. There are
a set of restricted characters in Strings that should be escaped using a `\`,
see [Escape-sequences](#Escape-sequences).

### EBNF Notation

```ebnf
escape = "\\" , "b" | "f" | "n" | "r" | "t" | "v" | "\\" | "'" ;
name = "a".."z" | "A".."Z" , { "a".."z" | "A".."Z" | "0".."9" } ;
template = "$" , name | ( "{" , expression, "}" ) ;
string = "'" , { any_character | template | escape } , "'" ;
```

<sub>`any_character` means all characters of the current character set
except for backslash, singlequote and dollar sign.</sub>

### Example

```ttr
'Hello, World!'

'Hello, $name'
'Hello, ${[expression]}'
```

<sub>See [expression](expressions.md) for details about expressions.</sub>

### Escape sequences

| Character(s) | Meaning             |
| ------------ | ------------------- |
| \n           | Newline             |
| \r           | Carriage Return     |
| \t           | Horizontal Tab      |
| \\           | Backslash           |
| \'           | Single Quote        |
