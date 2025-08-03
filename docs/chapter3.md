# Assembly

Logic
Data movement
Arithmetic
Control flow

As talked about in chapter 2, each CPU can have different features

There are a bunch of different features that depend on the actual CPU.
If you don't have a floating point unit you cannot perform floating point arithmetic in hardware and must emulate it - this will require different asm calls.

There are different families of instruction set architectures, some with optional includes.

CISC e.g. intel/AMD x86
1000's instructions

ARM is RISC
100-200 instructions

RISC-V
Is obviously RISC. 47 basic instructions
Optional but important extensions
M (multiply/divide)
A (atomics synchronisation)
F and D (single and double precision floating point)
C (compressed to 16 bits for efficiency)
V (vector extension for parallelisn)
B (more bit-manipulation instructions)

For simplicity (and because it is the future) we will be focusing on RISC-V. 









Runnging code
We're on chapter 3 - let's run some code.
We have created a .asm file. Note a file itself is just a series of bytes so we really are at the bottom.

This file is converted into binary machine code by the assembler.
How was the assembler written? Directly in binary! - originally.
Obviously once they had the first assembler they could use it to write the next one in assembly. This process of using a simple tool to build a better tool is called bootstrapping.


