# Statements

Statements define the program itself and what it will execute. Statements are a collection of what the language can do, these include for instance: expressions, functions and control flow.

__EBNF Notation__
```ebnf
statement =
  expression_statement |
  declaration |
  type_specification |
  comment |
  block |
  body |
  parameters |
  parameter |
  function |
  return;
```

<sub>See [expression](expressions.md) for details about expressions.</sub>  
<sub>See [functions](functions.md) for details about functions.</sub>  
<sub>See [control flow](control-flow.md) for details about control flow like choice and loops.</sub>

## Expressions

An expression is also a statement as some expressions can be used inline, like the assignment expression.

__EBNF Notation__
```ebnf
expression_statement = expression;
```

<sub>See [expression](expressions.md) for details about expressions.</sub>  

__Example__
```ttr
// "foo" has been declared beforehand

foo = 2

// An expression used as an statement
```

## Declaration

To work with variables you need to declare them first. A declaration exists of three parts. The first is the type of variable to declare: a var or val An optional [type specification](#Type-Specification) can be added after the var/val keyword to specify the type. When this is left out it will try to infer the type based on the givin expression. The last part of a declaration is the expression. When no value is needed and only the variable, the expression should be resolved as an identifier. When you need to assign a value to the variable the expression should resolve in an assignment expression.

__EBNF Notation__
```ebnf
declaration = "var" | "val" , ( [ ":" , name ] , expression | ":" , name , expression  );
```

__Example__
```ttr
val foo = 'string'
var: Integer bar = 64
val baz = 7 * 8
```

<sub>See [variables](variables.md) for details about variables.</sub>  
<sub>See [expression](expressions.md) for details about expressions.</sub>  

## Type Specification

Used to specify the type of a function or variable. This is in some cases optional as the compiler tries to infer the type when possible. In some cases it is mandatory to specify the type like in parameters.

__EBNF Notation__
```ebnf
type_specification = ":" , name;
```

__Example__
```ttr
val: string foo
val: Integer bar = 12

fun: string baz {
  return 'Hello World'
}

fun: string qux(name: string) {
  return 'Hello $name'
}
```

## Comment

Comments can be optionally parsed by the parser. This is for future use when comments can contain references to the actual code to describe certain features of said code (like [JSDoc](https://jsdoc.app/index.html)).

__EBNF Notation__
```ebnf
comment = comment_token;
```

__Example__
```ttr
val foo = true // This is an comment
```

## Block

A block statement is a collection of statements. This can contain any valid statement for the scope the block is used in.

__EBNF Notation__
```ebnf
block = { statement };
```

## Body

A body is the same as a block except that a body statements requires the curly brackets to be included in the statement.

__EBNF Notation__
```ebnf
block = "{" , { statement } , "}";
```

## Parameters

Used for passing variables or data to a function. It contains its parenthesis and a collection of [parameters](#parameter).

__EBNF Notation__
```ebnf
parameters = "(" , { parameter } , ")"
```

__Example__
```ttr
fun: string foo(name: string, age: integer){
  return '$name is $integer years old!'
}

// (name: string, age: integer)
// This part of the function is the parameter statement
```

## Parameter

A parameter is a used inside the [parameters](#parameters) statement to define a set of parameters. A paramater has a name and mandatory [type specification](#Type-Specification). The last part of the paramater statement is an optional comma token. When there is more then one parameter the comma is mandatory. when there is only one parameter or on the last parameter the comma is optional. This is also known as a trailing comma and is supported for parameters.

__EBNF Notation__
```ebnf
parameter = name , type_specification , [ "," ];
```

__Example__
```ttr
fun: string foo(name: string, age: integer){
  return '$name is $integer years old!'
}

// name: string,
// age: integer
// These two parts of the function are parameters

fun: string bar(name: string, age: integer,){
  return '$name is $integer years old!'
}

// name: string,
// age: integer,
// These are the same as stated above but age now has an trailing comma
```

## Function

A function statement is a complex statment to declare a function an consists of several parts some of which are optional (See [functions](functions.md)).

First is the fun keyword, after that is an optional [type specification](#Type-Specification). A type specification on a function mandates that the function returns a value from all paths. After that the function name should be declared. Then an optional statment for the [parameters](#parameters). Lastly the function [body](#body).

__EBNF Notation__
```ebnf
function = "fun" , [ type_specification ] , name , [ parameters ] , body;
```

__Example__
```ttr
fun foo {
    // Do something
}

fun bar(firstName: string, lastName: string) {
   // Do something
}

fun: string baz(firstName: string, lastName: string) {
   val greet = 'Hello' + firstName + lastName
   return greet
}
```

<sub>See [functions](functions.md) for details about functions.</sub>

## Return

Used for exiting a function or returning a value from a function. It consist of the return keyword and an optional expression that could be returned

__EBNF Notation__
```ebnf
return = "return" , [ expression ];
```

__Example__
```ttr
fun foo() {
   return
}

fun bar() {
   val a = 12
   return
   val b = a * 2
}

// val b = a * 2
// This part will never be executed

fun: string baz() {
   return 'Hello World'
}

fun: string qux() {
   return 12 * 4 + 2
}
```
