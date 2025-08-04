Now that we have finally laid the groundwork, let's talk about a real computer. We will go for a basic 64-bit single-core computer architecture.


Instruction fetch unit

Decode and disptatch:
Instruction decoder
Register rename unit
Issue queue/scheduler

Execution units:
Integer ALU
Float
Vector/SIMD
Load/store units - handle memory read write
Branch unit

Registers:
General purpose 
Program counters, status flags, stack pointer

Pipeline 
Fetch -> decode -> issue -> execute -> write-back

Out-of-order execution:
Reorder instructions dynamically to maximise usage in our execution units using reorder buffers and reservation stations

Cache - L1 L2 L3

CPU clock unit

Memory management unit - translation lookaside buffer

I/O
Interrupts, PCIE, RAM


