# SillySimple Architecture Upgrade
## Memory Added

In addition to the 8 Registers, the SillySimple Architecture has been upgraded to include 16 memory locations. Memory is similar to registers except values must be moved to and from them. Calculations are only done in the Registers.

>Memory: there are 16 memory locations number 0-15 (in binary). Memory is a place where data can be stored and retrieved. We do not perform calculations to values in memory. We must move them into registers first (using GET) and do the calculations. Then, if we want, we can move them back to memory (using STORE)
