<!-- TITLE: Computer Architecture -->
<!-- SUBTITLE: A quick summary of Computer Architecture -->

# What?
* main sole purpose of computer is to **execute programs**

# Basic Elements
* **Processor (CPU):**
	* heart, brain of the computer
	* all programs are executed by processor
	* program is a **set of instructions** stored in the memory 
	* main function of the CPU is to **fetch, decode and execute** these instructions
* **Main memory:**
	* primary/real memory
	* stores **programs and data**
	* various locations in memory is identified by its **own unique address** which contains some data
* **I/O modules:**
	* input -> computer -> output
	* **flow of information in and out**
* **System bus:**
	* connects all other parts
	* bus is a set of **interconnecting lines used to carry information**.


# Instructions
* An instruction cycle mainly involve **fetching**, decoding and **execution**

1. Program Counter (PC) gives the address to fetch an instruction from the memory.
2. The instruction [opcode](https://en.wikipedia.org/wiki/Opcode) is decoded. Decode: understanding/analysing the binary pattern of opcode.
3. This identifies, if there are any operands to be fetched from the memory. (and what operation to perform) Eg, **ADD** BL [BX+SI+3]
4. The operand address is calculated. Eg, ADD BL **[BX+SI+3]**
5. Operands are fetched from the memory. ADD **BL [BX+SI+3]**
6. Now the data operation is performed on the operands, and a result is generated.
7. If the result has to be stored in a register, the instruction ends here.
8. If the destination is memory, then the destination address has to be calculated.
9. The result is then stored in the memory.
10. Now the current instruction has been executed.
11. Side by side PC is incremented to calculate address of the next instruction.
12. The above instruction cycle then repeats for further instructions.



