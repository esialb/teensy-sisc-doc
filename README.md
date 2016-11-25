# Single-Instruction-Set Computer VM for Teensy 3.6

The Single-Instruction-Set Computer (**SISC**) is a CPU and associated Von Neuman architecture that has only has only a single instruction: Subtract and Branch if Negative (**SBN**).

SISC as implemented on Teensy has a 16-bit address space with 16-bit words.

Word bits are `0` through `15` inclusive, where bit `15` is the most-significant bit.

Negative numbers are not represented; all words are positive.  However, for purposes of subtraction, negatives are represented as if they were the bottom 16 bits of a twos-complement integer.

Instruction format:

```
SBN A, B, C
	**Subtract and Branch if Negative**
	NEG = Mem[B] > Mem[A]
	Mem[A] = Mem[A] - Mem[B]
	If NEG
		PC = C
	Else
		PC = PC+3

SBN A, B
	This is interpreted as SBN A, B, (PC + 3)
```

No registers are directly available to programs, however `PC` is memory-mapped to address `0xFFFF`.

All devices, including I/O devices, are memory-mapped to the negative address space.

## Examples

### Dereferencing a pointer

```
.macro-begin DEREFENCE(ptr_addr, dst_addr) {
	.code
	## set deref2 to -ptr_addr
		SBN deref2, deref2
		SBN deref2, ptr_addr
	## set deref+1 to -deref2 (== ptr_addr)
	## note: this is self-modifying code
		SBN (deref1+1), (deref1+1)
		SBN (deref1+1), deref2
	## set deref2 and dst_addr to zero
		SBN deref2, deref2
		SBN dst_addr, dst_addr
	.def deref1:
	## set deref2 to -Mem[ptr_addr]
	## this code is the self-modified instruction
		SBN deref2, 0 # B is overwritten by self-modifying code
	## set Mem[dst_addr] to Mem[ptr_addr]
		SBN dst_addr, deref2
	.data deref2:
		0
}
```