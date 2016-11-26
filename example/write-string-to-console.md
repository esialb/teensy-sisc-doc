# write direct string to console

```
.macro WRITE_STRING(string_addr) {
	SBN write_string_d1, write_string_d1
	SBN write_string_d2, write_string_d2
	SBN write_string_d2, string_addr
	SBN write_string_d1, write_string_d2
.code write_string_loop:
	DEREFERENCE(write_string_d1, write_string_d2)
	SBN HW_ZERO, write_string_d2, write_string_end
	SBN write_string_d3, write_string_d3
	SBN write_string_d3, write_string_d2
	SBN HW_CONSOLE_W, write_string_d3
	SBN HW_ZERO, HW_ONE, write_string_loop
.data write_string_d1:
	0
.data write_string_d2:
	0
.data write_string_d3:
	0
.code write_string_end:
}
```

# write indirect string to console

```
.macro WRITE_STRING_INDIRECT(string_addr_ind) {

}
```
