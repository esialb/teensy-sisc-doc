# Assembly language format

Two instruction formats:

```
SBN A, B, C
SBN A, B
```

*	`SBN A, B, C`
	
	Primary SBN instruction
*	`SBN A, B`
	
	Secondary format, interpreted as: `SBN A, B, $(PC+3)`
