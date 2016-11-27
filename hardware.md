# Memory Mapped Hardware Addresses

Reading from an address with no mapped device returns zero.  Writing to an address with no mapped device has no effect.

Write-only devices return zero when read. Read-only devices perform no action when written.


Address | Type | Symbol | Device | Read Behavior | Write Behavior
-----|-----|-----|-----|-----|-----
`0x0000` - `0x7FFF` | RW | `HW_RAM` | RAM | return RAM content | set RAM content
`0xFDFF` | W | `HW_OLED_W` | OLED console | | writes bottom 8 bits to OLED console
`0xFEFE` | R | `HW_SERIAL_R` | serial console| returns bottom 8 bits buffered from console `0xFEFF` | W | `HW_SERIAL_W` | serial console | | writes bottom 8 bits to serial console
`0xFFEE` | R | `HW_ONE` | One constant | Returns one | 
`0xFFEF` | R | `HW_ZERO` | Zero constant | Returns zero |
`0xFFFF` | RW | `HW_PC` | CPU PC register | return program counter of current instruction | set program counter of current instruction 
 

