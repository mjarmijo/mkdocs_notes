# ch 13 address spaces

Goal is to leave proceses in memory while switching between them in order to allow the OS to implement time sharing efficiently. Don't save memory to disk, it is too slow.

Address space is an easy to use abstraction of physical memory that the OS creates in conjunction with the hardware.

The address space contains all the memory state of the running program. The code/instructions, stack to track function call chain and local vars, and the heap, used for user managed dynamically allocated memory (malloc'ed), all exists in the address space.  Stack grows up from the limit of the address space, heap grows down.

OS has to make sure that when a program tries to load an instruction at address 0, it does not go to the actual physical address 0 but translates the virtual address 0 to some arbitrary address
