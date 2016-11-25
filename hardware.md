# Memory Mapped Hardware Addresses

Address | Device | Read Behavior | Write Behavior
-----|-----|-----|-----
`0xFFFF` | CPU PC register | return program counter of current instruction | set program counter of current instruction 
`0xFEFF` | serial console, write-only | returns `0` | writes bottom 8 bits to console
`0xFEFE` | serial console, read-only | returns bottom 8 bits buffered from console | ignored


