**What is an ISA?**
- Instruction Set Architecture
	- Interaction with Hardware must occur in a specific language
		- These are ***ISA's***
		- X86, Arm, and RISC-V are just a couple
	- ISA are composed of instructions that perform "basic" operations
		- Arithmetic
			- Add, Sub, Div, Mult,...
		- Memory
			- Load, store,....
	- Complex vs. Reduced
		- Complex means instructions can do more than one thing
		- Reduced means instructions are done one at a time
			- Requires more instructions to do the same thing but more simple units

**Why Choose RISC-V**
- Berkeley Developed RISC-V in 2010
- Unlike other Academic ISA's, made to **be used**
- Wanted to create a license free ISA
	- Royalty Free and Open Source
	- Heavily Supported!

**RISC-V**
- Instruction
	- What operation we'll do
- Destination
	- Where the register is stored to
- source1 and source2
	- What the arguments/operands of the instruction are
	- Both registers
- source1 & immediate
	- Immediate is a **constant fixed value**

```RISC-V
lw x28, 4(x5)
lw x29, 8(x5)
add x6, x28, x29
add x7, x6, x6
sw x7, 12(x5)
lw x10, 0(x5)
```