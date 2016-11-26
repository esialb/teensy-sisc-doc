# example: dereference a pointer

```
# Mem[dst_addr] = Mem[Mem[ptr_addr]]
.macro DEREFENCE(ptr_addr, dst_addr) {
	## set deref2 to -ptr_addr
	SBN deref2, deref2
	SBN deref2, ptr_addr
	## set deref+1 to -deref2 (== ptr_addr)
	## note: this is self-modifying code
	SBN $(deref1+1), $(deref1+1)
	SBN $(deref1+1), deref2
	## set deref2 and dst_addr to zero
	SBN deref2, deref2
	SBN dst_addr, dst_addr
	SBN HW_ZERO, HW_ONE, deref_end
.code deref1:
	## set deref2 to -Mem[ptr_addr]
	## this code is the self-modified instruction
	SBN deref2, 0 # B is overwritten by self-modifying code
	## set Mem[dst_addr] to Mem[ptr_addr]
	SBN dst_addr, deref2
.data deref2:
	0
.code deref_end:
}
```

