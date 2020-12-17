# Tutara Syntax

Tutara is an experimental programming language aimed at creating a reliable
sandboxed contextual function platform. This open-source platform enables the
ability to write scoped scripts. The platform can be embedded in software, or
used with the standard integrations. For example, the HTTP context supports
scripts to perform small actions like hashing a value or aggregating RSS feeds -
there are no limits to the possibilities.

::: tip
Tutara is still in a very early stage of development. Feel free to drop by on our
GitHub for any feedback.
:::

```ttr
fun: String greet(name: String) {
   val greet = 'Hello $name'
   return greet
}

val names = ['Niels', 'Marnix']
for (name in names) {
   print(greet(name))
}
```

## Get started today

- [A Tutara script](program.md)
- [Working with variables](variables.md)
- [Controlling the flow](control-flow.md)
- [Making use of functions](making-functions.md)
