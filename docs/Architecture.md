
# Architecture

## Address Bus Width and Word Length

In the realm of computer memory, the number of addresses that can be accessed is determined by the width of the address bus. This width represents the maximum number of unique addresses that the CPU can reference, akin to the number of unique boxes in our grid analogy. In our case, with a 16-bit address bus, the CPU can access up to 65,536 distinct memory locations, each identified by a unique address.

On the other hand, the word length pertains to the size of the data that can be stored at each memory address.  It defines the range of values that can be represented at a specific location in memory. With an 8-bit word length, each memory address can hold a value ranging from 0 to 255, providing a limited but essential range of numerical and character data that can be stored and manipulated by the CPU.

Together, the address bus width and word length form the foundational framework of computer memory, enabling the CPU to access and interact with a defined set of memory locations, each capable of holding a specific value within the constraints of the word length.

## Instruction Set

Our virtual CPU needs sn instruction set. These binary codes, while cryptic to humans, are the direct commands our CPU understands. For human readability, we pair each opcode with a mnemonic, like NOP for a no-operation instruction.

The instruction set features various operand types to support different operation needs:

* Implied operands are embedded within the instruction, requiring no additional data.
* Absolute operands provide a hard coded value to the operation.
* Direct addressing provide straightforward way to access specific memory locations.
* Indirect addressing introduces flexibility, allowing operations on data whose locations are held in another memory location.  
* Indexed addressing applies the value of a register (X or Y) as an offset to the value.  

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

## Interrupt Handling

In the realm of computer architecture, efficient management of tasks is paramount. Two fundamental components that facilitate this efficiency are Interrupt Requests (IRQs) and Interrupt Service Routines (ISRs). An IRQ is a hardware mechanism that allows peripheral devices to signal to the CPU that they require immediate attention. This signal typically manifests as a dedicated line that transitions to a low state, indicating an interrupt request.

Upon detecting an IRQ, the CPU momentarily suspends its current operations—a process known as interrupting. It then proceeds to execute an ISR, a predefined segment of code within the operating system specifically designed to handle the interrupt. The ISR is a critical section of software that addresses the needs of the interrupting device, ensuring that the system can continue to function without significant delays.

During the execution of an ISR, the CPU sets an acknowledgment line, known as IRQ_ACK, to a high state. This serves as an indication that the interrupt has been recognized and is being serviced. The CPU's role in this process is to save its current state before handling the interrupt, ensuring that it can resume its previous tasks without loss of information once the ISR is complete.

The ISR concludes with a Return from Interrupt (RTI) instruction, which signals the end of the interrupt service. Upon executing the RTI instruction, the CPU lowers the IRQ_ACK line, indicating that normal processing can resume. The device that initiated the IRQ, upon being serviced satisfactorily, releases the IRQ line, returning it to a high state and allowing the system to process other interrupts or continue with regular operations.

This interrupt-driven model is essential for real-time systems, where the ability to respond promptly to external events is crucial. It allows the CPU to address multiple concurrent demands efficiently, ensuring that high-priority tasks are serviced with minimal delay, while lower-priority tasks are not neglected. Through the use of IRQs and ISRs, a balance is struck between responsiveness and computational throughput, enabling complex systems to operate smoothly and reliably.

### The IRQ cycle

In our virtual system, the CPU's interaction with IRQs is a carefully orchestrated sequence that occurs in sync with the system's clock cycles. The CPU monitors the IRQ line during the low cycle of the bus clock, a period of relative inactivity where it is primed to detect any requests for attention. Should the IRQ line be found in a low state, signaling an interrupt request, the CPU promptly responds by setting the IRQ_ACK line high, an acknowledgment that the interrupt will be serviced.

The next steps involve the CPU preserving its current context to ensure a seamless return to its interrupted task later. It does this by pushing the state of its registers, along with the Program Counter (PC), onto the stack. This stack acts as a temporary storage that safeguards the CPU's state during the interrupt service.

With the current state secured, the CPU then retrieves the ISR vector from a designated location in main RAM. This vector is a pointer to the ISR's entry point within the operating system. The vector-based approach offers flexibility, allowing programmers to modify the ISR location if needed, providing a means to customize interrupt handling or to insert additional layers of interrupt processing.

As the system clock transitions to the next high cycle, the CPU is ready to execute the ISR. It is at this juncture that the CPU, now armed with the address of the ISR from the vector, begins the interrupt service. The ISR is executed with precision, addressing the needs that triggered the interrupt.

Upon completion of the ISR, a special instruction, RTI (Return from Interrupt), is issued. This instruction is the cue for the CPU to restore its previous state. The RTI instruction initiates the pop operation from the stack, reinstating the registers and the pre-interrupt PC. Concurrently, the IRQ_ACK line is lowered, signaling the end of the interrupt service.

The CPU, now restored to its prior state, continues from the exact point of interruption, resuming its process as though the interrupt had never occurred. This method, while straightforward, intentionally omits the complexity of handling nested interrupts, where one interrupt can be interrupted by another—a scenario that adds layers of complexity to the interrupt management system. Our virtual CPU design opts for simplicity to ensure clarity and reliability in the interrupt handling process. 

sampke 
| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|-----|----|----|----|---|---|---|---|
|  1  | 0  | 1  | 0 | 1 | 0 | 1 | 0 |

