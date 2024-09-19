A unit is a datatype that can only be equal to one thing:`()`
Basically, a filler to satisfy OCaml syntax:
```OCaml
let f (x : unit) : int = 3
// Can be written
let f () : int = 3
```
Since we don't use the x value, x can be put in as a `unit`
