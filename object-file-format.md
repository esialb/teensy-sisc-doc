# object file format

An object file is composed of 16-bit or 32-bit words, or UTF16 encoded strings.  Words may be signed or unsigned.

*	`uint16`: unsigned 16-bit word
*	`sint16`: signed 16-bit word
*	`uint32`: unsigned 32-bit word
*	`sint32`: signed 32-bit word
*	`string`: UTF16 encoded string

## [file]

```
[header]: file header
[sections]: relocatable code and data sections
```

## [header]
```
[magic]: magic byte sequence to identify files
[header_count: uint16]: header count
[header_section]{header_count}: headers
```

## [magic]
```
'SISC:16::': literal string, UTF16 encoded
```

## [header_section]
```
[header_type: uint16]: header type id
[header_length: uint32]: the length of the header data, in words
[header_data: uint16]{header_length}: header data words
```

## [header_type]
*	`0x0001`: Required Linker Symbol
	
	Namespace and name of a required linker symbol, UTF16 encoded string. Occurs once for each required linker symbol. Namespace and name are both null-terminated, with namespace prepended to name.
*	`0x0002`: Exported Linker Symbol

	Namespace and name of an exported linker symbol, UTF16 encoded string.  Occurs once for each exported symbol. Namespace and name are both null-terminated, with namespace prepended to name.