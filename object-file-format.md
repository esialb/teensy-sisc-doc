# object file format

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
*	`0x0000`: Linker Namespace
	
	Name of the linker namespace, UTF16 encoded string. May occur only once.
*	`0x0001`: Required Linker Namespace
	
	Name of a required linker namespace, UTF16 encoded string. Occurs once for each required linker namespace.
*	`0x0002`: Exported Linker Symbol
	
	Name of an exported linker symbol for this namespace, UTF16 encoded string.  Occurs once for each exported symbol.