# SillySimple Architecture
## Technical Manual


Computers seem mysterious, but in reality they only understand 1's and 0's. But how do they understand 1s and 0s?  Because in fact what they REALLY understand is the presence (1) or absence (0) of voltage.  They work on the same level as that lighbulb in your kitchen that turns on when the switch is in the "on" position and off when it's in the, well..., "off" position. Humans don't really get voltage/no voltage so we use 1/0 instead. But really we don't like 1/0 much either, so we translate the 1/0 into a code that provides instructions to the computer called machine code. Machine Code is a binary representation of the instructions (1's and 0's). We go one step further and translate the machine code into a readable programming language called assembly language which still isn't that pretty, so we then translate THAT into a programming language like C, Java or Python. These levels of translation are called Abstraction and this is our basis for being able to make computers do what we want.

### Machine Code
How does machine code work? Machine code works because it is the order and location of the 1s and 0s that provide info about what the computer should do.  There is a limited number of instructions the computer recognizes and everything we are able to do on a computer: we can do with these instructions. Very simple systems may have just a few instructions while more sophisticated ones have more.

### SillySimple Architecture
Snoodle Corp's computer system is very simple and only has 8 possible instructions numbered 0-7. 

In addition, the SillySimple system has two places where information is stored: registers and memory. Most instructions either use values stored in a register or a value encoded in the instruction itself. Two instructions GET and STORE retrieve (GET) or store (uh, STORE) a value in memory.

>Registers: there are eight registers numbered 0-7 (in binary). These are locations that store numbers short term. They are sort of like a whiteboard where you can save calculations.

>Memory: there are 16 memory locations number 0-15 (in binary). Memory is a place where data can be stored and retrieved. We do not perform calculations to values in memory. We must move them into registers first (using GET) and do the calculations. Then, if we want, we can move them back to memory (using STORE)

>Instructions: There are eight possible instructions. Each instruction is 16-bits (a bit is one binary digit) long. These instructions can be broken into parts that provide information about what they do. The first three bits tell you which instruction it is:

| 1st 3 Bits | Instruction | Description |
|--------------|-------------|-------------|
| 000 | ADD | This instruction adds the values in 2 registers and stores it in a third register.
| 001 | SUBTRACT | This instruction substracts the values in 2 registers and stores it in a third register.
| 010 | GREATER_THAN | This instruction compares the value in one register to another. If the number in the first register is greater than the one in the second register, it puts a 1 in the third register, otherwise it puts a zero. |
| 011 | LESS_THAN | This instruction compares the value in one register to another. If the number in the first register is less than the one in the second register, it puts a 1 in the third register, otherwise it puts a zero. |
| 100 | EQUAL_TO | This instruction compares the value in one register to another. If the number in the first register is equal to the one in the second register, it puts a 1 in the third register, otherwise it puts a zero.
| 101 | CLEAR | This sets the value of a register equal to 0
| 110 | STORE | This saves the value in a register to a specific memory location.
| 111 | GET | This retrieves a value from a memory location into a register

In the table above, the description for the ADD instruction says: "This instruction adds the values in 2 registers and stores it in a third register." How does the computer know what registers it should take values from and which registers it can use to store them? Each instruction has a form (they are all pretty similar). The locations of the 1s and 0s in the instruction provide information about what registers get used. Let's look at an example. 

>**Example:**
> An instruction might look like this: 0000010001000010. This is an ADD instruction. Let's break this one down. First let's break it into parts: 000 001 0 001 000 010.  The first three zeros indicate this is the ADD instruction. 

|             |                  Position                 | 
|-------------|-------------------------------------------|
| Instruction | 1-3      | 4-6 | 7 | 8-10 | 11-13 | 14-16 |
|-------------|----------|-----|---|------|-------|-------|
| ADD         | 000      | R3  | 0 | R1   | 000   | R2    |




