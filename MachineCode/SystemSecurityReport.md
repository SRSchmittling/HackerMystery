# System Security Report

The dark hackers attacked our system in two phases at different times. We discovered the initial values in the registers for both phases before any commands were executed, as well as the list of commands executed during each hack. 

We believe clues to their identity are embedded in the register values after all commands are executed. We seek to determine the name of the hacker, what high-level language they are using to implement machine code on our system and the location from which they completed their nefarious deeds.

We have narrowed down the possibilities through external intelligence:

Hacker Name is one of the following:

* Whiskers
* Hi-5
* Bl33p
* RayZ0r

The Hacker is using one of the following high-level languages:

* Boa
* Arrrrr
* MochaScript
* C++++

Our reconnaisance drones have narrowed down the location of our hacker to one of the following:

* Corner Grab & Go
* Evil Lair (aka hacker's bedroom)
* Mom's Basement
* High School Computer Lab

## Phase 1

### Initial Register Values Prior to Phase 1 Commands

| 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) |
|---------|---------|---------|---------|---------|---------|---------|---------|
|    0    |    0    |    0    |    1    |    0    |    4    |    0    |    8    |

### Commands Executed During Phase 1

1. 0101110101000000
2. 0000000011000001
3. 0011010001000100 
4. 0111010111000010 
5. 0001110100000110
6. 1000010101000011
7. 0000000001000010
8. 1111110000000000

### Fill in the Register For Each Instruction Executed During Phase 1

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


### Fill in Final Register Values for Phase 1 Here

| 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) |
|---------|---------|---------|---------|---------|---------|---------|---------|
| _______ | _______ | _______ | _______ | _______ | _______ | _______ | _______ |

* The number of the register that has a final value of 10 is a valid clue (in the list of Possible Clues from Phase 1 below).
* The value in Register 2 (010) is a valid clue.
* Two of the registers have the final value of 2. The sum of their numbers/addresses is a valid clue.

### Possible Clues From Phase 1 (Check Valid Clues)

   1. [ ] Hacker Name is related to shaving.

   2. [ ] Language is either a reptile or a tasty beverage.

   3. [ ] Hacker has a number in their name.

   4. [ ] The location is in a lab.

   5. [ ] The language has repeated characters.

   6. [ ] The location is not at home.

## Phase 2 

### Initial Register Values

| 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) |
|---------|---------|---------|---------|---------|---------|---------|---------|
|    1    |    1    |    0    |    0    |    2    |    3    |    7    |    0    |

### Commands Executed During Phase 2

1. 0101100101000111
2. 0000010111000000
3. 1111110000000000
4. 0110010100000010
5. 0001000001000110
6. 1000000100000101
7. 0001100001000011
8. 1110010000000000

### Fill in the Register For Each Instruction Executed During Phase 2

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


### Fill in Final Register Values for Phase 2 Here

| 0 (000) | 1 (001) | 2 (010) | 3 (011) | 4 (100) | 5 (101) | 6 (110) | 7 (111) |
|---------|---------|---------|---------|---------|---------|---------|---------|
| _______ | _______ | _______ | _______ | _______ | _______ | _______ | _______ |

* The final value in Register 5 is a valid clue.
* The maximum final value of all the registers is a valid clue
* The sum of the final value in Register 2 and Register 0 is a valid clue

### Possible Clues From Phase 2

   1. [ ] The name of the language is something pirates say.

   2. [ ] The location rhymes with Weevel Hair.

   3. [ ] You can't get a 32oz. Slurpy at the hacker's location!

   4. [ ] The hacker's name is a sound a computer makes.

   5. [ ] The hacker's name is an old-school fist bump.

   6. [ ] The language is a mediocre grade on an assignment (sort of).

