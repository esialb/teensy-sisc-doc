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

## Directives

### Sections

*	`.namespace <name>:`
	
	Begins a namespace section.  This namespace is inherited by all .code and .data sections that follow, unless another .namespace directive is encountered. This section directive may occur any number of times.
*	`.code [name (reloc|noreloc|export|noexport)*]:`
	
	Begins a section containing SBN instructions. This section directive may occur any number of times.
*	`.data [name (reloc|noreloc|export|noexport)*]:`
	
	Begins a section containing 16bit words as data included in the object file
### Section Modifiers

*	`reloc` This section may be relocated
*	`noreloc` This section must immediately follow the previous section
*	`export` The section is exported as a symbol
*	`noexport` This section is not exported as a symbol

Default section modifiers: `noreloc`, `noexport`


## Macros

*	`.macro <name>\(arg_list\) \{ body \}`
	
	Defines an assembly language macro. This directive may occur any number of times.

## Inline math

`$(<expression>)`

`<expression>` is a simple infix expression using label addresses, signed integer constants, and parentheses for grouping.

`PC` is a special label address, defined as (for `.code` sections) the offset of the current instruction from the containing section, or (for `.data` sections) the offset of the current word from the containing section.