# Memory Mapped Hardware Addresses

*Write-only devices return zero when read. Read-only devices perform no action when written.*

Address | Type | Device | Read Behavior | Write Behavior
-----|-----|-----|-----|-----
`0xFFFF` | RW | CPU PC register | return program counter of current instruction | set program counter of current instruction 
`0xFEFF` | W | serial console | | writes bottom 8 bits to serial console
`0xFEFE` | R | serial console| returns bottom 8 bits buffered from console | 
`0xFDFF` | W | OLED console | | writes bottom 8 bits to OLED console
 

