
# Architecture

## Address Bus Width and Word Length

In the realm of computer memory, the number of addresses that can be accessed is determined by the width of the address bus. This width represents the maximum number of unique addresses that the CPU can reference, akin to the number of unique boxes in our grid analogy. In our case, with a 16-bit address bus, the CPU can access up to 65,536 distinct memory locations, each identified by a unique address.

On the other hand, the word length pertains to the size of the data that can be stored at each memory address.  It defines the range of values that can be represented at a specific location in memory. With an 8-bit word length, each memory address can hold a value ranging from 0 to 255, providing a limited but essential range of numerical and character data that can be stored and manipulated by the CPU.

Together, the address bus width and word length form the foundational framework of computer memory, enabling the CPU to access and interact with a defined set of memory locations, each capable of holding a specific value within the constraints of the word length.

## Instruction Set

| Opcode | Mnemonic | Operand Size | Description |
|--------|----------|--------------|-------------|
| 0x00   | NOP      | 0 bits       | No operation, does nothing |
| 0x01   | BRK      | 0 bits       | Break, triggers an interrupt |
| 0x02   | RTS      | 0 bits       | Return from subroutine |
| 0x03   | PSH      | 0 bits       | Push accumulator onto the stack |
| 0x04   | POP      | 0 bits       | Pop the top value from the stack into the accumulator |
| 0x05   | TAX      | 0 bits       | Transfer accumulator to X register |
| 0x06   | TAY      | 0 bits       | Transfer accumulator to Y register |
| 0x07   | INX      | 0 bits       | Increment the value in the X register |
| 0x08   | DEX      | 0 bits       | Decrement the value in the X register |
| 0x09   | INY      | 0 bits       | Increment the value in the Y register |
| 0x0A   | DEY      | 0 bits       | Decrement the value in the Y register |
| 0x0B   | INC      | 0 bits       | Increment the value in the accumulator |
| 0x0C   | DEC      | 0 bits       | Decrement the value in the accumulator |
| 0x0D   | CLC      | 0 bits       | Clear carry flag |
| 0x0E   | RTI      | 0 bits       | Return from interrupt |
| 0x0F   | ASL      | 0 bits       | Arithmetic shift left of accumulator |
| 0x10   | ASR      | 0 bits       | Arithmetic shift right of accumulator |
| 0x11   | LSL      | 0 bits       | Logical shift left of accumulator |
| 0x12   | LSR      | 0 bits       | Logical shift right of accumulator |
| 0x13   | SEI      | 0 bits       | Set enable interrupt |
| 0x14   | SDI      | 0 bits       | Set disable interrupt |
| 0x15   | PSX      | 0 bits       | Push X register onto stack
| 0x16   | POX      | 0 bits       | Pop stack into register X
| 0x17   | PSY      | 0 bits       | Push Y register onto stack
| 0x18   | POY      | 0 bits       | Pop stack into register Y

| 0x40   | LDA #xx  | 8 bits       | Load accumulator with a specified value |
| 0x41   | LDX #xx  | 8 bits       | Load X register with a specified value |
| 0x42   | LDY #xx  | 8 bits       | Load Y register with a specified value |
| 0x43   | CMP #xx  | 8 bits       | Compare accumulator with a specified value |
| 0x44   | CPX #xx  | 8 bits       | Compare register X with a specified value |
| 0x45   | CPY #xx  | 8 bits       | Compare register Y with a specified value |

| 0x80   | JMP $xxxx | 16 bits     | Jump to a specified address |
| 0x81   | JSR $xxxx | 16 bits     | Jump to subroutine and save the return address |
| 0x82   | STA $xxxx | 16 bits     | Store accumulator at a specified memory address |
| 0x83   | STX $xxxx | 16 bits     | Store X register at a specified memory address |
| 0x84   | STY $xxxx | 16 bits     | Store Y register at a specified memory address |
| 0x85   | BNE $xxxx | 16 bits     | Branch if not equal |
| 0x86   | BEQ $xxxx | 16 bits     | Branch if equal |
| 0x87   | BLT $xxxx | 16 bits     | Branch if less than |
| 0x88   | BGT $xxxx | 16 bits     | Branch if greater than |
| 0x89   | LDA $xxxx,X | 16 bits   | Load accumulator with a value at address+offset by X |
| 0x8A   | LDA $xxxx,Y | 16 bits   | Load accumulator with a value at address+offset by Y |
| 0x8B   | BCC $xxxx | 16 bits     | Branch if carry clear |
| 0x8C   | BCS $xxxx | 16 bits     | Branch if carry set |
| 0x8D   | ADC $xxxx | 16 bits     | Add memory to accumulator with carry |
| 0x8E   | SBC $xxxx | 16 bits     | Subtract memory from accumulator with borrow |
| 0x8F   | ASL $xxxx | 16 bits     | Arithmetic shift left of memory location |
| 0x90   | ASR $xxxx | 16 bits     | Arithmetic shift right of memory location |
| 0x91   | LSL $xxxx | 16 bits     | Logical shift left of memory location |
| 0x92   | LSR $xxxx | 16 bits     | Logical shift right of memory location |
| 0x93   | JMP ($xxxx) | 16 bits     | Jump to a indirect address |
| 0x94   | SEI $xxxx | 16 bits     | Set SEI vector to location |
| 0x95   | BRK $xxxx | 16 bits     | Set BRK vector to location |
| 0x96   | LDA $xxxx | 16 bits     | Load accumulator with a value at address |
| 0x97   | LDX $xxxx | 16 bits     | Load X register with a value at address |
| 0x98   | LDY $xxxx | 16 bits     | Load Y register with a value at address |
| 0x99   | STA $xxxx,X | 16 bits   | Store accumulator with a value at address+offset by X |
| 0x9A   | STA $xxxx,Y | 16 bits   | Store accumulator with a value at address+offset by Y |
| 0x9B   | CMP $xxxx  | 16 bits    | Compare accumulator with memory location |
| 0x9C   | CPX $xxxx  | 16 bits    | Compare register X with memory location |
| 0x9D   | CPY $xxxx  | 16 bits    | Compare register Y with memory location |
| 0x9E   | ROL $xxxx | 16 bits     | Rotate shift left of memory location |
| 0x9F   | ROR $xxxx | 16 bits     | Rotate shift right of memory location |
| 0xA0   | ORA $xxxx | 16 bits     | Logical OR accumulator with value at address |


| 0xF0   | LDA $(xxxx)   | 16 bits     | Load accumulator with a value at indirect address |
| 0xF1   | LDA $(xxxx),X | 16 bits     | Load accumulator with a value at indirectaddress+offset by X |
| 0xF2   | LDA $(xxxx),Y | 16 bits     | Load accumulator with a value at indirectaddress+offset by Y |
| 0xF3   | STA $(xxxx)   | 16 bits     | Store accumulator with a value at indirectaddress+offset by X |
| 0xF4   | STA $(xxxx),X | 16 bits     | Store accumulator with a value at indirectaddress+offset by X |
| 0xF5   | STA $(xxxx),Y | 16 bits     | Store accumulator with a value at indirectaddress+offset by X |
| 0xF6   | JMP $(xxxx)   | 16 bits     | Jump to a indirect address |



