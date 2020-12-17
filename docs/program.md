# Script

A script runs within a specific context. This context is provided by the
platform it is running on. The current platform is the Tutara HTTP Platform
providing a HTTP context.

::: warning
The behavior of scripts is still an early concept and is subject to change.
:::

## HTTP Context

Below is an example of a script written within the HTTP context that checks the
body of a HTTP request and returns a response.

```ttr
use tutara.http.request
use tutara.http.response

val path = request.path

if (path == '/500') {
  response.status = 500
} else {
  response.status = 200
}
```

<sub>See [modules](modules.md) for details about importing and exporting code.</sub>
