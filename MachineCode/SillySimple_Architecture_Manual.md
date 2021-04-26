# SillySimple Architecture
## Technical Manual


Computers seem mysterious, but in reality they only understand 1's and 0's. More specifically, they understand the presence (1) or absence (0) of voltage. In your kitchen you observe the presence of voltage when you turn on a light switch and the light goes on. When the light is off, no voltage is presence (light switch is off). So computers "understand" voltage/ no voltage, but how are they able to perform work using only voltage / no voltage? Well humans created machine code which in coordination with hardware in the computer, allows computers to perform specific instructions. Machine Code is a binary representation of the instructions (1's and 0's). We go one step further and translate the machine code into a readable programming language called assembly language which still isn't that pretty, so we then translate THAT into a programming language like C, Java or Python. These levels of translation are called Abstraction and this is the basis for being able to make computers do what we want.

### Machine Code
How does machine code work? It is the order of the 1s and 0s that allow the computer to understand machine code. A system is designed to be able to interpret a certain number of instructions. Each instruction has a form the computer recognizes. The form it recognizes is called its Instruction Set Architecture. This manual provides a list of the instructions, and their form. In order to decode the instructions the dark hackers used on the system you will need to be able to read the instructions. This includes being able to identify binary numbers up to 7. This is not hard and there is a table at the end of the document with this information.

### SillySimple Architecture
Snoodle Corp's computer architecture is very simple and only has 8 possible instructions numbered 0-7. Two of the instructions are reserved for future use. They don't do anything at this time but are available for future use. 

In addition, the SillySimple system has 8 registers (numbered 0-7) which are places where information and calculations are stored. Registers store values up to 255. In addition, the SillySimple system is very basic and only stores positive numbers. So, if a calculation leads to a negative number, the result is 0. On the other hand, if a calculation is bigger than 255, it is capped at 255. 

>Instructions: There are eight possible instructions. Each instruction is 16-bits (a bit is one binary digit) long. These instructions can be broken into parts that provide information about what they do. The table below lists the 3-bit binary code for, the name and a description of these instructions. The first three bits tell you which instruction it is:

| 1st 3 Bits | Instruction | Description | Result of Execution |
|--------------|-------------|-------------|---------|
| 000 | ADD | Adds the values in one register (R1) to the value in another (R2) and stores it in a third (R3). | R3 = R1 + R2 |
| 001 | SUBTRACT | Substracts the value in one register from a value in another and stores it in a third register. | R3 = R1 - R2 | 
| 010 | GREATER_THAN | If the value in one register (R1) is greater than the value of another (R2), sets a third register (R3) equal to 1 (true), otherwise the third register is set to 0. | If R1 > R2, R3=1, else R3=0 |
| 011 | LESS_THAN | If the value in one register is less than the value of another, sets a third register equal to 1 (true), otherwise the third register is set to 0.  | If R1 < R2, R3=1, else R3=0 |
| 100 | EQUAL_TO | If the value in one register is equal to the value of another, sets a third register equal to 1 (true), otherwise the third register is set to 0. | If R1=R2, then R3=1, else R3=0 |
| 101 | for future use | not applicable | not applicable | 
| 110 | for future use | not applicable | not applicable |
| 111 | CLEAR | Sets the value in a register to 0. | R1 = 0 |

In the table above, the description for the ADD instruction says: "Adds the value in one register (R1) to the value in another (R2) and stores it in a  third (R3)." How does the computer know what registers it should take values from and which register to store the result to? Each instruction has a form (they are all pretty similar). The locations of the 1s and 0s in the instruction provide information about what registers get used. Let's look at an example. 

>**Example:**
> An instruction might look like this: 0001000011000010. This is an ADD instruction (R3 = R1 + R2). But how do we tell? Let's break this one down into parts: 000 100 0 011 000 010.  The first three zeros are the instruction number, 0, in binary. Because we use 3 bits (0s and 1s) for each instruction, every binary number always has 3 digits, even zero. The next three bits, '100', indicate what register the R1 value is in. In this case the value is in register 4. Then there is a 0, which is just a placeholder. The next 3 bits, '011', indicate what register the R2 value is in. In this case, the value is in register 3. Then there are 3 more zeros which are just placeholders. The final 3 bits, '010', indicate what register the value should be stored in (R3). In this case, the register is 2. 

So, let's say our registers have the following values (we are going to show all values in registers in decimal):

| 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) |
|---------|---------|---------|---------|---------|---------|---------|---------|
|    3    |    7    |    1    |    2    |    5    |    0    |    0    |    8    |

We issue the command 000 100 0 011 000 010. What register(s) above are changed? What are they changed to?

> Answer: when the command is executed it will perform R3 = R1 + R2. R1 is register 4, R2 is register 3, and R3 is register 2. This means we will set Register 2 equal to 5 + 2 = 7. Of course, neither register 4 or register 3 will change only register 2. Our registers will look like this:

| 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) |
|---------|---------|---------|---------|---------|---------|---------|---------|
|    3    |    7    |    7    |    2    |    5    |    0    |    0    |    8    |

Here is the format for all of the instructions:

| Instruction | 1-3      | 4-6 | 7 | 8-10 | 11-13 | 14-16 |
|-------------|----------|-----|---|------|-------|-------|
| ADD         | 000      | R1  | 0 | R2   | 000   | R3    |
| SUBTRACT    | 001      | R1  | 0 | R2   | 000   | R3    |
| GREATER_THAN | 010     | R1  | 0 | R2   | 000   | R3    |
| LESS_THAN    | 011     | R1  | 0 | R2   | 000   | R3    |
| EQUAL_TO     | 100     | R1  | 0 | R2   | 000   | R3    |
|     NA       | 101      | NA  | NA | NA | NA | NA |
|     NA       | 110      | NA  | NA | NA | NA | NA |
| CLEAR        | 111      | R1  | 0 | 000 | 000 | 000 |

The Subtract, Greater_Than, Less_Than and Equal_To instructions are all laid out the same way as the ADD instruction. For the Clear instruction only the first 6 bits are used. The first three are '111' which is the instruction number (7), the next 3 bits represent the number of the register that will be cleared in binary.

Appendix B has a Worksheet with answers that will ensure that you understand the SillySimple Architecture fully.


# APPENDIX A
## Binary numbers up to 255

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

Commands Issued:

1. 0000000001000101
2. 0101010111000011
3. 0011110101000010
4. 1111010000000000
5. 0110110100000000
6. 0001000000000010
7. 1001110010000100
8. 1111010000000000
9. 0001100111000101
10. 0011110110000000

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


| Instruction | 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) | Result (Register #s appear in parentheses) |
|-------------|---------|---------|---------|---------|---------|---------|---------|---------|--------|
|       1     |    3    |   7     |   7     |   2     |    **5**    |  10     |   0     |    8    | R3 (5) = R1 (0) + R2 (1) |
|       2     |    3    |   7     |   7     |   2     |    5    |  10     |   **1**     |    8    | R1 (5) > R2 (7), **R3 (6)=1**, else R3 (6)=0 |
|       3     |    3    |   7     |   **0**     |   2     |    5    |  10     |   1     |    8    | R3 (2) = R1 (7) - R2 (5) |
|       4     |    3    |   7     |   0     |   2     |    5    |  10     |   1     |    8    | R1 (5) = 0 | PROBLEM, FIX
|       5     |    3    |   7     |   0     |   2     |    5    |  10     |   1     |    8    | R1 (3) < R2 (4), R3 (0)= 1, else **R3 (0) =0** |
|       6     |    3    |   7     |   8     |   2     |    5    |  10     |   1     |    8    | R3 (2) = R1 (4) + R2 (0) |
|       7     |    3    |   7     |   8     |   2     |    1    |  10     |   1     |    8    | R1 (7) = R2 (2), **R3 (4)=1**, else R3 (4)= 0
|       8     |    3    |   7     |   8     |   2     |    1    |  0      |   1     |    8    | R1 (5) = 0
|       9     |    3    |   7     |   8     |   2     |    1    |  9      |   1     |    8    | R3 (5) = R1 (6) + R2 (7) 
|      10     |    7    |   7     |   8     |   2     |    0    |  0      |   1     |    8    | R3 (0) = R1 (7) - R2 (6) 

Final Values in registers:

| 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) |
|---------|---------|---------|---------|---------|---------|---------|---------|
|    3    |    7    |    7    |    2    |    5    |    0    |    0    |    8    |
