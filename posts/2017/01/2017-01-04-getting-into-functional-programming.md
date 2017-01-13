The most tricky part is to get used to new function signature notation.

```elm
slice : Int -> Int -> String -> String
```

In imperative language it would be `function slice(start, end, string)` which
returns a substring. But using currying, `slice` is defined as a sequence of
functions, each with a single argument.

See https://en.wikipedia.org/wiki/Currying for details.
