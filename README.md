# Single-Instruction-Set Computer VM for Teensy 3.6

The Single-Instruction-Set Computer (**SISC**) is a CPU and associated Von Neuman architecture that
has only has only a single instruction: Subtract and Branch if Negative (**SBN**).

SISC as implemented on Teensy has a 64-bit address space with 16-bit words.

Word bits are `0` through `15` inclusive, where bit `15` is the most-significant bit.

Bit `15` is the sign bit, using twos-complement binary representation.

Instruction format:

```
SBN A, B, C
```

Registers:
```
PC: program counter
NEG: negative flag
```

Semantics:

```
NEG = Mem[B] > Mem[A]
Mem[A] = Mem[A] - Mem[B]
if NEG
	PC = C
else
	PC = PC + 3
```

No registers are directly available to programs, however `PC` is memory-mapped to address `0xFFFF`.

