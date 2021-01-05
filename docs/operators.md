# Operators

Operators are split into two categories: arithmetic operators and assignment
operators. Arithmetic operators can be used to manipulate literals and
variables. assignment operators can be used in the same way but include a
mandatory assignment to a variable.

```ebnf
arithmetic_operator = "+" | "-" | "*" | "/" | "**" | "%" ;
assignment_operator = "=" | "+=" | "-=" | "*=" | "/=" | "**=" | "%=" ;
```

## Arithmetic operators

Arithmetic operators include the fundamental operators of arithmetic.

### Plus

The plus operator is used for adding two values.

#### Example

```ttr
5 + 7
1 + 1 + 2
'foo' + 'bar'
```

### Minus

The minus operator is used for subtracting two values.

#### Example

```ttr
3 - 2
1 - 3 - 5
```

### Multiply

The multiply operator is used for multiplying two values.

#### Example

```ttr
3 * 1
3 * 5
```

### Division

The division operator is used for dividing. Divide by zero is an illegal
operation and thorws a runtime error.

#### Example

```ttr
9 / 2
12 / 4
191 / 0 <- Not allowed
```

### Exponentiation

The exponentiation operator is used for power levy.

#### Example

```ttr
2 ** 64
3 ** 2
42 ** 0
```

### Modulo

The modulo operator is used for getting the remainder of a division.

#### Example

```ttr
9 % 2
13 % 7
```

## Assignment operators

Assignment operators are used as a shorthand expression when performing an
optional operation and assignment at the same time.

### Assign

The basic assign operator for assigning a literal or expression to a variable.
See [variables](variables.md)

#### Example

```ttr
var foo = 'bar'
var bar = 3
```

### Plus assign

Plus assign can be used to add a value to an existing variable and directly
assigning the new value to itself.

#### Example

```ttr
var foo = 3
foo += 1

var bar = 'string'
bar += 'another string'
```

### Minus assign

Minus assign can be used to subtract a value of an existing variable and
directly assigning the new value to itself.

#### Example

```ttr
var foo = 9
foo -= 7

var bar = 17
bar -= 5
```

### Multiply assign

Multiply assign can be used to multiply a value with an existing variable and
directly assigning the new value to itself.

#### Example

```ttr
var foo = 3
foo *= 3

var bar = 2
bar *= 12
```

### Divide assign

Divide assign can be used to divide a variable by an value and directly
assigning the new value to itself.

#### Example

```ttr
var foo = 9
foo /= 3

var bar = 22
bar /= 11
```

### Exponentiation assign

Exponentiation assign can be used to power levy a variable by an value and
directly assigning the new value to itself.

#### Example

```ttr
var foo = 2
foo **= 8

var bar = 50
bar **= 1
```

### Modulo assign

Modulo assign can be used to get the remainder of an division by a value and an
existing variable and directly assigning the new value to itself.

#### Example

```ttr
var foo = 48
foo %= 3

var bar = 3
bar %= 2
```

### And assign

When using the 'and assign' operation you can perfrom an 'and condition' on a
variable and another boolean value.

#### Example

```ttr
var foo = true
foo &= 1 == 1

var bar = false
bar &= 12 == 4
```

### Or assign

When using the 'or assign' operation you can perfrom an 'or condition' on a
variable and another boolean value.

#### Example

```ttr
var foo = 2 == 4
foo |= 2 == 2

var bar = false
bar |= 12 == 4
```
