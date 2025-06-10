# The Process

A **process** is a running program. A program is a bunch of instructions on disk. The operating system gets these running and transforms the program into something useful.

How does the OS provide the illusion of many CPUs?

The OS creates the illusion of many CPUs by virtualizing the CPU. By running one process, then quickly stopping and running another, the OS can create an illusion that dozens of CPUs exist when in fact there is one (or a few). This techinque is known as **time sharing the CPU.**

**Mechanisms** are the low-level methods and protocols that implement a piece of functionality. For example, a context switch gives the OS the ability to stop running one program and start running another on a given CPU.

On top of mechanisms, **policies** are the intelligence algorithms for making some kind of decision in the OS. A scheduling policy decides which program to run from a list of potentially runnable programs.

## The abstraction of a running program: A process

The abstraction the OS provides of a running program is called a process. To understand a process we have to understand what constitutes its state at any point in time.

One important component of state include its machine state, which is made up of memory (i.e. address space), CPU registers and I/O information (i.e. which file are open).  Special CPU registers include the program counter (i.e. instruction pointer), stack pointer and frame pointer are used to manage th stack (points to function parameters, address spaces, and local variables).

## The process API

Process APIs include system calls to create and destroy processes and manage them. Examples include `fork()`, `exec()`, `wait()` and `exit()`. Other management tasks include getting status information and other controls suche as suspending and resuming the process.

Process creation

1. The first thing the OS must do is load its code and static data from disk into memory in the address space of the process. Modern OSes perform this task lazily, meaning that the code is loaded only as they are needed during program execution.
2. The OS must allocate memory for the program's stack and heap. The stack is used to manage function calls and local variables, while the heap is used for dynamically allocated memory (e.g., memory allocated with `malloc()` and freed with `free()`, data structures like linked lists, hash tables, and trees).
3. Each process has three open file descriptors for standard input, standard output and standard error. The OS must set these up so that the process can read input from the terminal and write output to the screen.
4. Finally the OS will start the program running at the entry point `main()` and the transfer control of the CPU to the process to begin execution.
5. The OS will also set up the process control block (PCB) which contains all the information about the process, including its state, memory usage, open files, and other resources.

## Process states

A process can be in one of several different states at a given time:

- Running: a process is running on the processesor and executing instructions
- Ready: A process is ready to run, but the OS is choosing not to run it at this moment.
- Blocked: A process has performed some kind of operation that makes it not ready until another event takes place. For example, when a process initiates I/O requests to disk, it is blocked and another process can use the processor. Once I/O completes (or some other event causing blocking, like waiting on a network packet) the process is moved to Ready.

Scheduling: Being moved from ready to running means the process has been scheduled. Moved from running to ready means the process has been descheduled. Decsions on which processes to run and when are made by the Scheduler.

## Data Structures

The OS has key data structures that track various pieces of process information, such as the state of each process. The OS keeps a process list (aka task list) for all ready processes, blcoked processes, When a processes is blocked the contents of the process's registers must be saved to memory. When the process resumes the registers are restored by moving them from memory to the physical registers on the CPU so the process resumes. This is called a context switch.

Process control block (PCB): The structure that stores information about a given process (program counter, stack pointer, PID etc)

![Process control block](./images/process-control-block.png)
