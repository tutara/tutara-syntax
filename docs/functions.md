# Functions

Functions are used for encapsulating specific behavior in a program te be reused with given parameters. Functions are described by the `fun` keyword. They return a value with the `return` keyword which takes an expression as right-hand. Everything after a return is considered unreachable code. 

To specify the returned type of a function a semicolon (`:`) is written after the `fun` keyword. After this a identifier is required to set the name of the function. Functions can receive parameters via parentheses (`(` and `)`). Parameters are declared inside separated by a comma (`,`). Parameters require a type specification using a semicolon (`:`) followed by the type. 

A function needs a body with the statements that execute when the function is called. Function bodies are declared by placing an opening curly brace (`{`) to start, and an closing curly brace (`}`) to end it. A function with a specified return type must always return the given type. Functions without return types may use the return keyword to end early.

__EBNF Notation__
```ebnf
name = "a".."z" | "A".."Z" , { "a".."z" | "A".."Z" | "0".."9" } ;
function = "fun" , [ ":", name ] , name , [ "(" , [ name , ":" , name , "," ] , { name , ":" , name } ")" ] , "{" { statement } , "}" ;
```

<sub>* `statement` is a placeholder</sub>

__Example__
```ttr
fun foo {
    // Do somthing
}

fun bar(parameter: string) {
    // Do somthing
}

fun baz(firstName: string, lastName: string) {
   // Do somthing
}

fun: string qux {
   return 'value'
}

fun: string quux(parameter: string) {
   parameter = 'Hello' + parameter
   return parameter
}

fun: string quuz(firstName: string, lastName: string) {
   val greet = 'Hello' + firstName + lastName
   return greet
}
```
