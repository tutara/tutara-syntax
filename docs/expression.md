# Expression

To work with mathematics, boolean logic and variables you will use expressions. 

## Order of operations:

Expression have an order of operations in how they are resolved, this also determines what an expressions output may be of said expression.

| N. | Implemented   | Operation token     | Context                                   |
|----|---------------|---------------------|-------------------------------------------|
| 1	 | [ ]           | TBD                 | Function call, scope, array/member access |
| 2	 | [ ]           | TBD                 | unary operators, sizeof and type casts    |
| 3	 | [x]           | * / %               | Multiplication, division, modulo          |
| 4	 | [x]           | ^                   | Involution                                |
| 5	 | [x]           | + -	               | Addition and subtraction                  |
| 6	 | [ ]           | << >>               | Bitwise shift left and right              |
| 7	 | [ ]           | < <= > >=	         | Comparisons: less-than and greater-than   |
| 8	 | [ ]           | == !=               | Comparisons: equal and not equal          |
| 9	 | [ ]           | &                   | Bitwise AND                               |
| 10 | [ ]           | TBD                 | Bitwise exclusive OR (XOR)                |
| 11 | [ ]           | \|                  | Bitwise inclusive (normal) OR             |
| 12 | [ ]           | &&                  | Logical AND                               |
| 13 | [ ]           | \|\|                | Logical OR                                |
| 14 | [ ]           | TBD                 | Conditional expression (ternary)          |
| 15 | [x]           | = += -= *= /= %= ^= | Assignment operators                      |
| 16 | [x]           | 1, true, name       | Identifier & Literal  (terms)             |

<sub>This list is still in concept and will subject to change</sub>  
<sub>see: [operators](operators.md)</sub>

__EBNF Notation__
```ebnf
expression = 
  identifier_expression | 
  literal_expression | 
  binary_expression | 
  unary_expression | 
  grouping_expression | 
  assignment_expression;
```

## Identifier expression

Identifiers are references to the name of a variable declared inside of a scope. These share a spot in the order of operations with literals under the combined name: terms. An identifier expression cannot exist on its own and is thus always nested within other expressions. 

__EBNF Notation__
```ebnf
identifier_expression = name;
```

__Example__
```ttr
var a = 12
a = 2

// a is the identifier expression thats nested in a assignment expressions.

val b = a / 7

// a and b are both identifier expression that are nested within an expression tree.
```

## Literal expression

Like identifiers, literals are expressions based on a single item. In this case a literal value like: 1, true/false or 'string'. These share a spot in the order of operations with identifiers under the combined name: terms. Like identifiers, these cannot exit on their own and are always nested within another expression.

__EBNF Notation__
```ebnf
literal_expression = boolean | integer | string;
```
<sub>see: [primitives](primitives.md)</sub>

__Example__
```ttr
var a = 12
a = 2

// 12 and 2 are both literal expressions.

val b = a / 7

// 7 is an literal expression.

var c = true
c = false

// true and false are both literal expressions.

var d = 'Niels'
d = 'Marnix'

// 'Niels' and 'Marnix' are both literal expressions.
```

## Binary expression 

Used in performing an operation on two expressions. These are used to build the expression tree. The last leaf within the tree will always be a term (identifier or literal). Binary expression are used for mathematical operations, logic operations, assignment expressions and any valid combination between these. Binary expressions follow the [order of operations](#Order-of-opperations).

Since binary expressions contain expressions for the left and right side of the operations it can go to a very deep nesting of expressions. In the example image below there is an example of how the binary expression tree is build.

Expression: (a + b) * c + 7

![Expression tree of the expression (a+b)*c+7](https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/Exp-tree-ex-11.svg/500px-Exp-tree-ex-11.svg.png)

<sub>Source: [wikimedia](https://commons.wikimedia.org/wiki/File:Exp-tree-ex-11.svg)</sub>

For more information on how expression trees work and are build see the [wikipedia article](https://en.wikipedia.org/wiki/Binary_expression_tree) on binary expression tree's.

__EBNF Notation__
```ebnf
binary_expression = expression, operator, expression;
```

<sub>see: [operators](operators.md)</sub>

__Example__
```ttr
var a

a = 2 * 3 

// 2 * 3 
// is a binary expression of 2 terms with an multiply operation.

var b

b = a / 1

// a / 1 
// is a binary expression of 2 terms with an division operation.

val c = a * b + 12 / 2

// a * b + 12 / 2 
// is a binary expression of two binary expressions. When resolving these it will result as follows
// binary expression left: a * b (Which is a also binary expressions)
// operation: Add (+)
// binary expression right 12 / 2 (Which is a also binary expressions)

// The end result of c = 42
```

## Unary expression  

Used for applying a single operator to an expression. For instance: using a minus operator to invert the state of an mathematical expression.

__EBNF Notation__
```ebnf
unary_expression = minus, expression;
```

__Example__
```ttr
var a = 12
a = - 12

// - 12
// is a unary expression that inverts the state of literal to a negative number
```

## Grouping expression

A grouping is used for telling the interpreter to resolve the grouped expression first. This is used to resolve an nested expression with an higher order of operation before one with an lower one. Using the grouping expression to change the order of operations also changes the outcome. The classic example is [PEMDAS](https://pemdas.info) for basic mathematical expressions.

__EBNF Notation__
```ebnf
grouping_expression = "(", expression, ")";
```

__Example__
```ttr
// Using the normal order of operations
// the 5 * 2 is resolves first and then it will add the 1.

1 + 5 * 2

// Results in 11

// Using the grouping expression we force
// the interpreter to resolve the 1 + 5 first
// and multiply with 2 afterwards.

(1 + 5) * 2

// Results in 12
```

## Assignment expression

Used for binding a result of an expression to a variable. This can be used in deceleration and as expression. It consists of the name of the variable that will bind the expression result. The type of assignment. For instance: a basic assignment that takes the expression results and assigns it to the variable; addition assignment for adding the result of the expression to the existing value of the variable or division assignment that divides the existing value of the variable with the result of the expression.

__EBNF Notation__
```ebnf
assignment_expression = name, assignment_operator, expression;
```

__Example__
```ttr
var a = 1
a = 2

// a = 2

var b = 12
b += 4

// b = 16

var c = 9
c /= 3

// c = 3

var d = 2
d ^= 8

d = 256
```

<sub>see: [variables](variables.md)</sub>  
<sub>see: [operators](operators.md)</sub>
