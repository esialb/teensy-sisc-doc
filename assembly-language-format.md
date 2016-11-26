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
*	`.data [name]`
*	`.macro <name>(arg_list) { body }`

## Inline math

`$(<expression>)`

Expression is a simple infix expression using label addresses, signed integer constants, and parentheses for grouping.