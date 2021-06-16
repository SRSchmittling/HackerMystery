# System Security Report

The dark hackers attacked our system in two phases at different times. We discovered the initial values in the registers for both phases before their commands were executed, as well as a list of commands they executed. 

We believe clues to their identity are embedded in the register values after all commands are executed. We seek to determine their hacker name, the high-level language they are using to implmement machine code on our system and the location from which they are completing their nefarious deeds.

We have narrowed down the possibilities through external intelligence:

Hacker Name is one of the following:

* Whiskers
* Hi-5
* Bl33p
* RayZ0r
* BuzzLightYr

The Hacker is using one of the following high-level languages:

* Boa
* Arrrrr
* MochaScript
* C++++
* Sapphire

Our reconnaisance drones have narrowed down the location of our hacker to one of the following:

* Corner Grab & Go
* Evil Lair (aka hacker's bedroom)
* Mom's Basement
* High School Computer Lab
* Tea Lab (Local Boba Tea joint)

## Phase 1

### Initial Register Values For Phase 1

| 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) |
|---------|---------|---------|---------|---------|---------|---------|---------|
|    0    |    0    |    0    |    1    |    0    |    4    |    0    |    8    |

### Commands Executed During Phase 1

1. 010 111 0 101 000 000 | R7 > R5, R0 = 1
2. 000 000 0 011 000 001 | R1 = R0 + R3
3. 001 101 0 001 000 100 | R4 = R5 - R1 
4. 011 101 0 111 000 010 | R5 < R7, R2 = 1 
5. 000 111 0 100 000 110 | R6 = R7 + R4
6. 100 001 0 101 000 011 | R1 = R5, R3 = 0
7. 000 000 0 001 000 010 | R2 = R0 + R1
8. 111 111 0 000 000 000 | R7 = 0

### Fill in the Register For Each Instruction Executed During Phase 1

| Instruction | 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) |
|-------------|---------|---------|---------|---------|---------|---------|---------|---------|
|       1     | **1**   |   0     |   0     |   1     |   0     |   4     |   0     |   8     |
|       2     |   1     | **2**   |   0     |   1     |   0     |   4     |   0     |   8     |
|       3     |   1     |   2     |   0     |   1     | **2**   |   4     |   0     |   8     |
|       4     |   1     |   2     | **1**   |   1     |   2     |   4     |   0     |   8     |
|       5     |   1     |   2     |   1     |   1     |   2     |   4     | **10**  |   8     |
|       6     |   1     |   2     |   1     | **0**   |   2     |   4     |   10    |   8     |
|       7     |   1     |   2     | **3**   |   0     |   2     |   4     |   10    |   8     |
|       8     |   1     |   2     |   3     |   0     |   2     |   4     |   10    | **0**   |

### Fill in Final Register Values for Phase 1 Here

| 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) |
|---------|---------|---------|---------|---------|---------|---------|---------|
|    0    |    2    |    3    |    1    |    2    |    4    |   10    |   8     |

* The number of the register that has a final value of 10 is a valid clue (in the list of Possible Clues from Phase 1 below).
* The value in Register 2 (010) is a valid clue.
* Two of the registers have the final value of 2. The sum of their numbers/addresses is a valid clue.

### Possible Clues From Phase 1 (Check Valid Clues)

   1. [ ] Hacker Name is related to shaving.

   2. [ ] Language is either a reptile or a tasty beverage.

   3. [X] Hacker has a number in their name.

   4. [ ] The location is in a lab.

   5. [X] The language contains characters that repeat in a row.

   6. [X] The location is not at home.

## Phase 2 

### Initial Register Values for Phase 2

| 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) |
|---------|---------|---------|---------|---------|---------|---------|---------|
|    1    |    1    |    0    |    0    |    2    |    3    |    7    |    0    |

### Commands Executed During Phase 2

1. 010 110 0 101 000 111 | R6 > R5, R7 = 1
2. 000 001 0 111 000 000 | R0 = R1 + R7
3. 111 111 0 000 000 000 | R7 = 0
4. 011 001 0 100 000 010 | R1 < R4, R2 = 1
5. 000 100 0 001 000 110 | R6 = R4 + R1
6. 100 000 0 100 000 101 | R0 = R4, R5 = 1
7. 000 110 0 001 000 011 | R3 = R6 + R1
8. 111 001 0 000 000 000 | R1 = 0

### Fill in the Register For Each Instruction Executed During Phase 2

| Instruction | 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) |
|-------------|---------|---------|---------|---------|---------|---------|---------|---------|
|       1     |    1    |    1    |    0    |    0    |    2    |    3    |    7    |  **1**  |
|       2     |  **2**  |    1    |    0    |    0    |    2    |    3    |    7    |    1    |
|       3     |    2    |    1    |    0    |    0    |    2    |    3    |    7    |  **0**  |
|       4     |    2    |    1    |  **1**  |    0    |    2    |    3    |    7    |    0    |
|       5     |    2    |    1    |    1    |    0    |    2    |    3    |  **3**  |    0    |
|       6     |    2    |    1    |    1    |    0    |    2    |  **1**  |    3    |    0    |
|       7     |    2    |    1    |    1    |  **4**  |    2    |    1    |    3    |    0    |
|       8     |    2    |  **0**  |    1    |    4    |    2    |    1    |    3    |    0    |

### Fill in Final Register Values for Phase 2 Here

| 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) |
|---------|---------|---------|---------|---------|---------|---------|---------|
|    2    |    0    |    1    |    4    |    2    |   1     |   3     |    0    |

* The final value in Register 5 is a valid clue.
* The maximum final value of all the registers is a valid clue
* The sum of the final value in Register 2 and Register 0 is a valid clue

### Possible Clues From Phase 2

   1. [X]  The name of the language is something pirates say.

   2. [ ] The location rhymes with Weevel Hair.

   3. [X] You can't get a 32oz. Slurpy at the hacker's location!

   4. [X] The hacker's name is a sound a computer makes.

   5. [ ] The hacker's name is an old-school fist bump.

   6. [ ] The language is a mediocre grade on an assignment (sort of).

## Solution
**Hacker Name:**  Bl33p
**Language:**  Arrrrr
**Location:** High School Computer Lab