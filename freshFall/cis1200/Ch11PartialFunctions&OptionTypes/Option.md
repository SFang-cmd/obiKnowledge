Consider the datatype:
```OCaml
type 'a option = 
| None 
| Some of 'a
```

Creates a new datatype where nothing is an option:

```OCaml
let rec list_max (l:int list) : int option = 
	begin match l with 
	| [] -> None
	| x::tl -> begin match (list_max tl) with 
			| None -> Some x 
			| Some m -> Some max x m end end
```
Note: Prevents errors bc of None and Some m both are represented by "int option" datatype