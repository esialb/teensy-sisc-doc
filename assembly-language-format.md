# Assembly language format

## Instructions

Two instruction formats:

```
SBN A, B, C
SBN A, B
```

*	`SBN A, B, C`
	
	Primary SBN instruction
*	`SBN A, B`
	
	Secondary format, interpreted as: `SBN A, B, $(PC+3)`

## Sections

*	`.code [name]`
	
	Begins a section containing SBN instructions.
*	`.data [name]`
	
	Begins a section containing 16bit words as data included in the object file
*	`.macro <name>(arg_list) { body }`
	
	Defines an assembly language macro

## Inline math

`$(<expression>)`

`<expression>` is a simple infix expression using label addresses, signed integer constants, and parentheses for grouping.