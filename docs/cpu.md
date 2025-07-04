# CPU
> (for opcodes, see [opcodes.md](opcodes.md)!)

## Registers
The CPU has 16 registers, named `R0`-`Rf`. All of them are 8-bit. They're used for storing data for quick access and for calculations - data from memory must first be copied into a register and then processed. `Rf` is often set by math operations to whether an overflow occured during that operation, so be careful when using it.

Additionally, the CPU has two 16-bit "registers" called `Ri` and `Rj`, representing the memory pointer and the disk pointer respectively.

## Program counter
Since PC64K has 64KB of memory, the program counter is 16-bit.

## Frequency
Up to you! (100Khz in my implementation, 1 instruction = 1 cycle)

## Stack
Up to you! (128 16-bit values / 256 bytes in my implementations)