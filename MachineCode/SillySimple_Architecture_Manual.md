# SillySimple Architecture
## Technical Manual


Computers seem mysterious, but in reality they only understand 1's and 0's. More specifically, they understand the presence (1) or absence (0) of power (i.e., voltage). In your kitchen you observe the presence of power when you turn on a light switch and the light goes on. When the light is off, no power is presence (light switch is off). So computers "understand" power/ no power, but how are they able to perform work using only voltage / no power? Well humans created machine code which in coordination with hardware in the computer, allows computers to perform specific instructions. Machine Code is a binary representation of the instructions (1's and 0's). We go one step further and translate the machine code into a readable programming language called assembly language which still isn't that pretty, so we then translate THAT into a programming language like C, Java or Python. These levels of translation are called Abstraction and this is the basis for being able to make computers do what we want.

### Machine Code
How does machine code work? It is the order of the 1s and 0s that allow the computer to understand machine code. A system is designed to be able to interpret a certain number of instructions. Each instruction has a form the computer recognizes. The form it recognizes is called its Instruction Set Architecture. This manual provides a list of the instructions, and their form. In order to decode the instructions the dark hackers used on the system you will need to be able to read the instructions. This includes being able to identify binary numbers up to 7. This is not hard and there is a table at the end of the document with this information.

### SillySimple Architecture
The Snoodle Corp's SillySimple system is very simple (surprise, surprise). It is composed of instructions and registers. It has only 8 possible instructions which are numbered 0 to 7. Two of these instructions are reserved for future use. They don't do anything at this time but could be added later. Because the registers and instructions are both identified using values between 0 and 7 in binary, it is important that you can recognize the binary values for values in this range. If you don't know binary, **Appendix A** shows the binary representation for the numbers 0-7.  

The system has 8 registers also numbered 0 to 7. Registers are just places to store information, usually calculations which result from instructions. They store values up to 255. In addition, the SillySimple system only stores positive numbers. So, if a calculation leads to a negative number, the result stored in the register will be 0. On the other hand, if a calculation is bigger than 255, the value stored is 255. We will refer to specific registers using R and their decimal code, i.e., R1 is register 1, R2 is register 2, etc. 

>Instructions: There are eight possible instructions. Each instruction is 16-bits (a bit is one binary digit) long. These instructions can be broken into parts that provide information about what they do. 

>**Example:**
>
> * An instruction might look like this: 0001000011000010. This is an ADD instruction. But how do we tell? Let's break this one down into parts: 000 100 0 011 000 010.  The first three zeros are the instruction number, 0, in binary. Because we use 3 bits (0s and 1s) for each instruction. Every instruction always has 3 digits, even zero. The next three bits, '100', indicate what register the first source value is in (SR1). In this case the value is in register 4. Then there is a 0, which is just a placeholder. The next 3 bits, '011', indicate what register the second source value (SR2) is in. In this case, the value is in register 3. Then there are 3 more zeros which are just placeholders. The final 3 bits, '010', indicate what register the value should be stored in or the destination register (DR). In this case, the register is 2. 

So, let's say our registers have the following values (we are going to show all values in registers in decimal):

| 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) |
|---------|---------|---------|---------|---------|---------|---------|---------|
|    3    |    7    |    1    |    2    |    5    |    0    |    0    |    8    |

We issue the command 000 100 0 011 000 010. What register(s) above are changed? What are they changed to?

> Answer: when the command is executed it will perform DR = SR1 + SR2. SR1 is register 4, SR2 is register 3, and DR is register 2. This means we will set Register 2 equal to 5 + 2 = 7. Of course, neither register 4 or register 3 will change only register 2. Our registers will look like this:

| 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) |
|---------|---------|---------|---------|---------|---------|---------|---------|
|    3    |    7    |    7    |    2    |    5    |    0    |    0    |    8    |

The table below lists the 3-bit binary code for, the name and a description of these instructions. DR = destination register, SR = source register. If more than one source register used in command, they will be numbered: SR1, SR2, etc.

| 1st 3 Bits | Instruction | Description | Result of Execution |
|--------------|-------------|-------------|---------|
| 000 | ADD | Adds the values in one register (SR1) to the value in another (SR2) and stores it in a third (DR). | DR = SR1 + SR2 |
| 001 | SUBTRACT | Substracts the value in one register (SR2) from a value in another (SR1) and stores it in a third register (DR). | DR = SR1 - SR2 | 
| 010 | GREATER_THAN | If the value in one register (SR1) is greater than the value of another (SR2), set a third register equal to 1 (DR=1), otherwise the third register is set to 0 (DR=0). | If SR1 > SR2, DR=1, else DR=0 |
| 011 | LESS_THAN | If the value in one register (SR1) is less than the value of another (SR2), set a third register equal to 1 (DR=1), otherwise the third register is set to 0 (DR=0).  | If SR1 < SR2, DR=1, else DR=0 |
| 100 | EQUAL_TO | If the value in one register (SR1) is equal to the value of another (SR2), set a third register equal to 1 (DR=1), otherwise the third register is set to 0 (DR=0). | If SR1==SR2, then DR=1, else DR=0 *|
| 101 | for future use | not applicable | not applicable | 
| 110 | for future use | not applicable | not applicable |
| 111 | CLEAR | Sets the value in a register (DR) to 0. | DR = 0 |

* here == means "equal to" in order to set it apart from = which indicates "set to".

In the table above, the description for the ADD instruction says: "Adds the value in one register (A1) to the value in another (A2) and stores it in a  third (A3)." How does the computer know what registers it should take values from and which register to store the result to? Each instruction has a form (they are all pretty similar). The locations of the 1s and 0s in the instruction provide information about what registers get used. Let's look at an example. 

Here is the format for all of the instructions:

| Instruction | 1-3      | 4-6 | 7 | 8-10 | 11-13 | 14-16 |
|-------------|----------|-----|---|------|-------|-------|
| ADD         | 000      | SR1  | 0 | SR2   | 000   | DR    |
| SUBTRACT    | 001      | SR1  | 0 | SR2   | 000   | DR    |
| GREATER_THAN | 010     | SR1  | 0 | SR2   | 000   | DR    |
| LESS_THAN    | 011     | SR1  | 0 | SR2   | 000   | DR    |
| EQUAL_TO     | 100     | SR1  | 0 | SR2   | 000   | DR    |
|     NA       | 101      | NA  | NA | NA | NA | NA |
|     NA       | 110      | NA  | NA | NA | NA | NA |
| CLEAR        | 111      | DR  | 0 | 000 | 000 | 000 |

Every instruction is composed of 16 bits. However, not all bits are used in every instruction. Unused bits are set to 0 as placeholders. The Subtract, Greater_Than, Less_Than and Equal_To instructions are all laid out the same way as the ADD instruction. Only the first 6 bits of the Clear instruction only the first 6 bits are set. The first three are '111' which is the instruction number (7), the next 3 bits represent the number of the register in binary that will be cleared, the remaining zeros are just placeholders.

>Example: to clear register 5, the instruction would be **111 101 0000000000**. The instruction is broken up to make it easier to read.

Appendix B has a Worksheet with an answer key. This Worksheet will let you know if you understand how the SillySimple Architecture works.


# APPENDIX A
## Binary numbers up to 7

|Decimal | Binary|
|--------|-------|
| 0 | 000 |
| 1 | 001 |
| 2 | 010 |
| 3 | 011 |
| 4 | 100 |
| 5 | 101 |
| 6 | 110 |
| 7 | 111 |

# APPENDIX B
## SillySimple Architecture Worksheet

Complete this worksheet to ensure you fully understand how to decode SillySimple Architecture commands.  We provide you with the starting values for the 8 SillySimple Registers. Following are 10 instructions which are executed on the system. You need to 1) translate the instruction; 2) Perform the instruction on paper; 3) Update any register; and, 4) continue to the next instruction and repeat the process.  Appendix C has the answers when you are done.  **HINT:** Break each code into its correct parts before trying to decode it.

> Initial Register Values

The initial values for the registers are:

| 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) |
|---------|---------|---------|---------|---------|---------|---------|---------|
|    3    |    7    |    7    |    2    |    5    |    0    |    0    |    8    |

Commands Issued (the first 3 are separated for you):

1. 000 000 0 001 000 101 
2. 010 101 0 111 000 011
3. 001 101 0 111 000 010
4. 1110010000000000
5. 0110110100000000
6. 0000100011000001
7. 0001000010000110
8. 1001110110000100
9. 1110110000000000
10. 0011100010000000

Fill in the table below by providing the values of each register after the instruction # in the first column has been executed.

| Instruction | 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) |
|-------------|---------|---------|---------|---------|---------|---------|---------|---------|
|       1     |         |         |         |         |         |         |         |         |
|       2     |         |         |         |         |         |         |         |         |
|       3     |         |         |         |         |         |         |         |         |
|       4     |         |         |         |         |         |         |         |         |
|       5     |         |         |         |         |         |         |         |         |
|       6     |         |         |         |         |         |         |         |         |
|       7     |         |         |         |         |         |         |         |         |
|       8     |         |         |         |         |         |         |         |         |
|       9     |         |         |         |         |         |         |         |         |
|      10     |         |         |         |         |         |         |         |         |


# APPENDIX C
## Worksheet Answer

Initial Values in registers:

| 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) |
|---------|---------|---------|---------|---------|---------|---------|---------|
|    3    |    7    |    7    |    2    |    5    |    0    |    0    |    8    |


| Instruction | 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) | Result (Values in Registers appear in parentheses) |
|-------------|---------|---------|---------|---------|---------|---------|---------|---------|--------|
|       1     |    3    |   7     |   7     |   2     |    5    |  **10**     |   0     |    8    | R5 (10) = R0 (3) + R1 (7) |
|       2     |    3    |   7     |   7     |   **1**     |    5    |  10     |   0     |    8    | if R5 (10) > R7 (8), **R3 = 1**, else R3=0 |
|       3     |    3    |   7     |   **2**     |   1     |    5    |  10     |   0     |    8    | R2 (2) = R5 (10) - R7 (8) |
|       4     |    3    |   **0**     |   2     |   1     |    5    |  10     |   0     |    8    | R1 = 0 | 
|       5     |    **1**    |   0     |   2     |   1     |    5    |  10     |   0     |    8    | if R3 (1) < R4 (5), **R0 = 1**, else R0 = 0 |
|       6     |    1    |   **3**     |   2     |   1     |    5    |  10     |   0     |    8    | R1 (3) = R2 (2) + R3 (1) |
|       7     |    1    |   3     |   2     |   1     |    5    |  10     |   **7**     |    8    | R6 (7) = R4 (5) + R2 (2) |
|       8     |    1    |   3     |   2     |   1     |    **0**    |  10      |   7     |    8    | if R7 (8) == R6 (7), R4 = 1, else **R4 = 0** |
|       9     |    1    |   3     |   2     |   **0**     |    0    |  10      |   7     |    8    | R3 = 0 |
|      10     |    **5**    |   3     |   2     |   0     |    0    |  10      |   7     |    8    | R0 (5) = R6 (7) - R2 (2) |

Final Values in registers:

| 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) |
|---------|---------|---------|---------|---------|---------|---------|---------|
|    5    |    3    |    2    |    0    |    0    |    10   |    7    |    8    |
