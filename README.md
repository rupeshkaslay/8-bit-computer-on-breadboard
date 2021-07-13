# 8-Bit Computer On Breadboard
Design and implement your own CPU and computer using basic digital building blocks on a digital circuit simulator. We implement the CPU as per Ben Eater's popular video series on the topic: https://www.youtube.com/watch?v=HyznrdDSSGM&amp;list=PLowKtXNTBypGqImE405J2565dvjafglHU

# Background
During the COVID-19 lockdown, I was looking for good electronics project to pass time. A friend sent me a link to Ben Eater's video series (link above) which immediately appealed to me. He implemented the CPU on a set of breadboards with basic digital ICs. However, due to the COVID-19 lockdown, I was not able to procure the components required to implement it physically. So I thought of implementing it on a digital simulator and it turned out to be a great learning experience.

Since Ben has an extensive 44 video playlist that explains all the core concepts and design, no additional documentation is offered here. Please acquire a basic understanding from that playlist.

# Tools
The project is implemented using a free (but excellent!) Digital Logic Designer and Simulator: https://github.com/hneemann/Digital. The tool comes with good documentation and a host of example circuits.

# Implementation
The computer is implemented using basic digital building blocks:
- Logic Gates
- Registers
- Buffers
- Counters
- Adders
- Comparators
- Multiplexers

To aid understanding, and to map as closely as possible to Ben's physical implementation, the implementation is divided in to functional blocks:
- Clock (CLK.dig)
- Memory Access Register (MAR.dig)
- Instruction Register (IR.dig)
- Program Counter (PC.dig)
- General Purpose Register (Reg.dig)
- ALU (ALU.dig)
- Flags Decoder (FlagsDecoder.dig)
- Helper Circuit for ALU (Flag.dig)

You can step through one clock pulse at a time to fully understand what is going on. In addition, outputs labeled "**-DGB**" are provided to observe the data at various parts of the circuit.

![Debug](https://github.com/rupeshkaslay/8-bit-computer-on-breadboard/blob/main/images/Debug.JPG)

A complete manual override is provided, with all internal signals available.

![Manual Switch-board](https://github.com/rupeshkaslay/8-bit-computer-on-breadboard/blob/main/images/ManualSwitchBoard.JPG)

If you switch on the **Manual** switch, you can set any signal using the switchboard

## Instruction Set
Instruction | Explanation
----------- | -----------
FETCH | Fetch next instruction from memory pointed by Program Counter. Used largely as NOP instruction
LDA M | Fetch data pointed to by Memory Access Register (MAR) and put it in Register A
ADD M | Fetch data pointed to by Memory Access Register (MAR) and add it to data in Register A. The result is stored in Register A
SUB M | Fetch data pointed to by Memory Access Register (MAR) and subtract it from data in Register A. The result is stored in Register A
STA M | Store current contents of Register A at memory location pointed to by Memory Access Register (MAR)
LDI A | _Immediate load_ Load data byte following this instruction in to Register A
