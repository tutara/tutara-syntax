# Logic

There are three basic logic operators: 'or', 'and' and 'not'. Using these you can fully use boolean algebra. Besides the basic three there are more operators that combine combinations of these three to reduce the footprint of logic expressions.

Comparison operators are used in comparing values on a left- and right-hand side to evaluate to a boolean value.

## Logic operators

__EBNF Notation__
```ebnf
logic_operator = "!" | "&&" | "||" ;
```

### Not

The not operator is a unary operator used for inverting the boolean state.

__Example__
```ttr
val foo = true
val bar = !foo

// the value of 'bar' is 'false'
```

### And

Compares two comparison expressions and evaluates if both resolved values are true and returns true if so.

__Logical table__

| P     | Q     | P ^ Q |
|-------|-------|-------|
| true  | true  | true  |
| true  | false | false |
| false | true  | false |
| false | false | false |

__Example__
```ttr
val foo = true
val bar = true

var baz = foo && bar

// the value of 'baz' is 'true'

baz = false && bar

// the value of 'baz' is 'false'
```

### Or

Compares two comparison expressions and evaluates if either resolved value is true and returns true if so.

__Logical table__

| P     | Q     | P ∨ Q |
|-------|-------|-------|
| true  | true  | true  |
| true  | false | true  |
| false | true  | true  |
| false | false | false |

__Example__
```ttr
val foo = true
val bar = true

var baz = foo || bar

// the value of 'baz' is 'true'

baz = false && bar

// the value of 'baz' is 'true'
```

## comparison operators

__EBNF Notation__
```ebnf
comparison_operator = "==" | "!=" | "<=" | ">=" | "<" | ">" ;
```

### Equality

Compares two expressions on equality. If both sides' value are the same it evaluates to true.

__Logical table__

| P     | Q     | P ↔ Q |
|-------|-------|-------|
| true  | true  | true  |
| true  | false | true  |
| false | true  | true  |
| false | false | false |

__Example__
```ttr
val foo = true
val bar = true

var baz = foo == bar

// the value of 'baz' is 'true'

baz = false == bar

// the value of 'baz' is 'false'

if (baz == false) {
  baz = true
}

// The end result for 'baz' is 'true'
```

### Disjunction

Compares two expressions on non equality. If both sides' value differ it evaluates to true.

__Logical table__

| P     | Q     | P ⊕ Q |
|-------|-------|-------|
| true  | true  | true  |
| true  | false | true  |
| false | true  | true  |
| false | false | false |

__Example__
```ttr
val foo = true
val bar = true

var baz = foo != bar

// the value of 'baz' is 'false'

baz = false != bar

// the value of 'baz' is 'true'

if (baz != false) {
  baz = false
}

// The end result for 'baz' is 'false'
```

### Greater or equal to

Compares two expressions on value size. If the left hand's value is greater or equal to the right hands it evaluates to true.

__Example__
```ttr
val foo = 12
var bar = 6

if (foo >= bar) {
  // foo is greater than bar
}

bar = 12

if (foo >= bar) {
  // foo is equal to bar
}
```

### Lesser or equal to

Compares two expressions on value size. If the left hand's value is lesser or equal to the right hands it evaluates to true.

__Example__
```ttr
val foo = 6
var bar = 12

if (foo <= bar) {
  // foo is smaller than bar
}

foo = 12

if (foo <= bar) {
  // foo is equal to bar
}
```

### Greater than

Compares two expressions on value size. If the left hand's value is greater than the right hands it evaluates to true.

__Example__
```ttr
val foo = 12
var bar = 6

if (foo > bar) {
  // foo is greater than bar
}

bar = 14

if (foo > bar) {
  // this block wont be reached
}
```

### Lesser than

Compares two expressions on value size. If the left hand's value is lesser than the right hands it evaluates to true.

__Example__
```ttr
val foo = 12
var bar = 6

if (foo < bar) {
  // this block wont be reached
}

bar = 14

if (foo < bar) {
  // foo is lesser than bar
}
```
