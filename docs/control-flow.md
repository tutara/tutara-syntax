# Control flow

The control flow is a fundamental part of the language allowing the code to
branch off. The control flow is divided into two groups: choice and loops.

<sub>See [expressions](expressions.md) for details about expressions.</sub>  
<sub>See [statements](statements.md) for details about statements.</sub>  

## Choice

There are two expressions in the choice group. if- and match-expressions.

If-expressions consist of three parts: the if, else-if and else. The first two
accept an expression that evaluates to either `true` or `false`. The latter is
a fallback if none of the preceding expressions evaluate to `true`.

All branches accept a body of statements that are evaluated depending on the
branch's expression. Code bodies may be wrapped between curly braces to allow
multiple statements.

The match-expression is a syntactic sugar for the if-expression allowing more
readable code. It has two variants: parameterized and non-parameterized.

The parameterized variant takes the expression after the match keyword in
parenthesis. The following body accepts a match-rule on the given parameter.
Each rule will perform an equals check with the given expression.
The non-parameterized variant does not take a parameter after the match keyword
but takes expressions to evaluate. Both match variants accept an default clause
when no rules match using the "else" keyword.

### EBNF Notation

```ebnf
name = "a".."z" | "A".."Z" , { "a".."z" | "A".."Z" | "0".."9" } ;

if = "if" , "(" , expression , ")" , ( "{" , { statement } , "}" | expression ) ;
else = "else" , ( "{" , { statement } , "}" | expression ) ;
else_if = "else" , if ;
if_statement = if , { else_if } , [ else ] ;

match = "match" , [ "(" , expression , ")" ] , "{" , { ( expression | "else" ) , "->" , ( "{" , { statement } , "}" | expression ) }  "}" ;
```

### Example

```ttr
// Match with argument
val result = match (x) {
  10 -> 'x is exactly 10'
  else -> 'x is not 10'
}

// Match without argument
val result = match {
  x < 10 -> 'x is below 10'
  x == 10 -> 'x is exactly 10'
  x > 10 -> 'x is above 10'
}

match {
  foo == bar -> {
    // foo is bar
  }
  foo == baz -> {
    // foo is baz
  }
  else -> {
    // foo is not bar and not baz
  }
}

// If without curly braces
val result = if (x < 10) 'x is below 10'
  else if (x == 10) 'x is exactly 10'
  else if (x > 10) 'x is above 10'


// If with curly braces
val result = if (x < 10) {
  'x is below 10'
} else if (x == 10) {
  'x is exactly 10'
} else if (x > 10) {
  'x is above 10'
}
```

## Loops

There are three types of looping control flows: loop, while and for. Loops can
be stopped prematurely by adding a break statement in the flow.

The loop statement is a syntactic sugar for a `while (true)` loop. In a loop
statement you can add a set of statements to be executed. This loop will go on
infinitely unless a break condition is hit in the flow.

The while loop takes an expression to be evaluated to a true or false condition
an will execute the statements inside the body. As long as the condition in the
while expression evaluates to true the loop will go on unless a break condition
inside the loop is met.

Lastly the for loop can perform a set of statements based on an expressing with
the addition of adding an index within the loop to access.

### EBNF Notation

```ebnf
name = "a".."z" | "A".."Z" , { "a".."z" | "A".."Z" | "0".."9" } ;

break = "break"

while = "while" , "(" , expression , ")" , "{" { statement } , "}" ;
loop = "loop" , "{" { statement } , "}" ;

for = "for" , "(" , name , "in" , expression , ")" , "{" { statement } , "}" ;
```

### Example

```ttr
// loop
var i = 0
loop {
  i++
  if (i == 10) break
}

// while
var i = 0
while (i < 10) {
  i++
}

// for
for (j in 1..10) {

}
```
