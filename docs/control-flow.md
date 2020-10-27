# Control flow

The control flow is a fundamental part of the language allowing the code to branch off. The control flow is divided into two groups: choice and loops.

# Choice

There are two expressions in the choice group. if- and match-expressions.

The if-expression consists of three parts: the if, else-if and else. The first two accept an expression that resolves to either `true` or `false`. The latter is a fallback if none of the preceding expressions resolved to `true`.

All of these branches accept a body of statements that are executed depending on the branch's expression. Code bodies may be wrapped between curly braces to allow multiple statements.

The match-expression is a fancy version of the if-expression allowing more readable code. It has two variants: an argumented and non argumented one. 

The argumented version takes the expression after the match keyword in parenthesis. The following body accepts a matching expression on the given argument. This expression starts with an comparing operator and inserts the identifier before that when resolving.

The non argumented version does not take an argument after the match keyword but takes expressions on the identifier to match on. Each new match must start with said identifier and an matching comparing operator. After that normal expression rules apply.

__EBNF Notation__
```ebnf
name = "a".."z" | "A".."Z" , { "a".."z" | "A".."Z" | "0".."9" };

if = "if" , "(" , expression , ")" , ( "{" , { statement } , "}" | statement );
else = "else" , ( "{" , { statement } , "}" | statement );
else-if = "else" , if;
if-statement = if , { else-if } , [ else ];

match-statement-equal = expression;
match-statement-operator = ( "!" | "==" | ">" | "<" | ">=" | "<=" ) , expression;
match-statement-range = expresion ".." expression;
match-statement-set = expression [ { "," expression } ];
match-statement-function = [ name ] , [ "." ] , name;
match-expression = match-statement-equal | match-statement-operator | match-statement-range | match-statement-set | match-statement-function;
match-arg = "match" , "(" , expression , ")" , "{" , { match-expression , "->" , ( "{" , { statement } , "}" | statement ) }  "}";

match-no-arg = "match" , "{" , { expression , "->" , ( "{" , { statement } , "}" | statement ) }  "}";
match-statement = match-arg | match-no-arg;
```

__Example__
```ttr
// Match with argument
val result = match (x) {
  < 10 -> 'x is below 10'
  == 10 -> 'x is exactly 10'
  > 10 -> 'x is above 10'
}

// Match without argument
val result = match {
  x < 10 -> 'x is below 10'
  x == 10 -> 'x is exactly 10'
  x > 10 -> 'x is above 10'
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

There are three types of looping control flows: loop, while and for. Loops can be stopped prematurely by adding a break statement in the flow. 

The loop statement is a way of cleanly stating a `while (true)` loop. In a loop statement you can add a set of statements to be executed. This loop will go on infinitely unless a break condition is added in the flow.

The while loop takes an expression to be evaluated to a true or false condition an will execute the statements inside the body. As long as the condition in the while expression evaluates to true the loop will go on unless a break condition inside the loop is met.

Lastly the for loop can perform a set of statements based on an expressing with the addition of adding an index within the loop to acces.

__EBNF Notation__
```ebnf
name = "a".."z" | "A".."Z" , { "a".."z" | "A".."Z" | "0".."9" };

break = "break"

while = "while" , "(" , expression , ")" , "{" { statement } , "}";
loop = "loop" , "{" { statement } , "}";

for = "for" , "(" , name , "in" , expression , ")" , "{" { statement } , "}";
```

__Example__
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
for (i in 1..10) {

}
```
