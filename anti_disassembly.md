#Anti-Disassembly

There are two techniques to perform disassembly: 

**- Linear disassembly**

- Iterates over a block of code disassembling one instruction at a time linearly, without deviating. 

- Unable to differentiate between code and data

- The key way malware writers exploit this strategy is by planting data bytes that can be manipulated as multi-byte instructions.

Example:
If the 16 bytes of data that compose a switch table end with 0xE8, disassembler will think that the next 4 bytes are part of call instruction. Call instruction starts with E8.  

**- Flow-oriented disassembly**

- Conditional branches give the disassembler a choice of two places to disassemble: true or false branch. In handwritten assembly code and anti-assembly code, two branches can often produce different disassembly for the same block of code.

- Due to this, disassemblers can commit mistakes while disassembling even when they are following flow of code.

- In IDA Pro, you can manually switch bytes from code to data or data to code.

- Data to code : C

- Code to data : D


####Anti-Disassembly Techniques

- Jump instructions with the same target. Back to back conditional jump to the same location. The combination is in effect a jmp instruction but the disassembler does not know this. So disassembler continues to disassemble the false branch even though it will never be executed. 

- Single conditional jump when the condition will always be the same. Disassembler analyzes the false branch first and it trusts it more. This leads to wrong disassembly. 

- Impossible disassembly: An opcode is part of two valid instructions which will both be executed. But since no disassembler can analyze / categorize such a byte, it will disassemble according to its own trust. It is possible that overall effect of a set of such instructions is something simpler. As a malware analyst, we should NOP other bytes and convert them into a set of instructions which produce the same result. 

####Obscuring Flow control

- Function pointer problem: 
Function pointers and calls to functions through function pointers are not detected/ cross referenced by IDA Pro. 

- Return Pointer abuse: 
retn can be used to jump to any instruction on the stack.
When retn is used for purposes other than returning from a function, disassemblers fail. Disassembler does not show an cross reference to the target being jumped to. Also, it will prematurely terminate the function in which retn appears. 

*To adjust function boundaries, use ALT-P*



