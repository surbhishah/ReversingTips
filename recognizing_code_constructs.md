Recognizing code constructs
-

####Global Vs Local variables:

- Local variables are on the stack and will be accessed using ebp.

- Global variables are accessed in memory directly. In assembly, it will look like dword_MEMORY.

####If statements: 

- There must be a conditional jump for an if statement.

- The code just after conditional jump executes if condition fails. Generally, this code executes when the condition is true and is skipped if condition is false with the help of conditional jump.

####For loops: 

- 4 parts: Initialization, comparison, execution instructions and increment/decrement.

- General structure: 

			init
			jmp to compare
			
			back:
			increment/decrement
			
			compare: 
			checks condition 
			jump to exit if condition is not met
			execution instructions
			Jump to back
			exit: 
			

####while loops

- General structure

			Check condition
			Jump to exit if condition is not met
			Execution instructions
			Jmp to Check condition
			exit:
			
####Function call conventions
These conventions include the order in which parameters are placed on stack or in registers and whether caller or callee is responsible for cleaning the stack when the fucntion is complete.

- cdecl:
Parameters are pushed onto stack from right to left. 
Caller cleans up stack when the function is complete. 

- stdcall:
Parameters are pushed onto stack from right to left. 
**Callee** cleans up stack when the function is complete.
Calling convention for Windows API

- fastcall:
First few arguments (generally 2) are passed in registers - edx and ecx
Additional arguments are pushed onto stack from right to left.
Caller is responsible for cleaning up stack.

####switch statements
#####If style
Used when there are few switch conditions. Just like nested if-else
#####Jump table
Used when there are more switch conditions. Depends on compiler.
Jump table contains addresses to jump to if any of the conditions is true. 








