# The Process

A **process** is a running program. A program is a bunch of instructions on disk. The operating system gets these running and transforms the program into something useful.

How does the OS provide the illusion of many CPUs?

The OS creates the illusion of many CPUs by virtualizing the CPU. By running one process, then quickly stopping and running another, the OS can create an illusion that dozens of CPUs exist when in fact there is one (or a few). This techinque is known as **time sharing the CPU.**

Mechanisms are the low-level methods and protocols that implement a piece of functionality. For example, a context switch gives the OS the ability to stop running one program and start running another on a given CPU.

On top of mechanisms, policies are the intelligence algorithms for making some kind of decision in the OS. A scheduling policy decides which program to run from a list of potentially runnable programs.

## The abstraction of a running program: A process

The abstraction the OS provides of a running program is called a process. To understand a process we have to understand what constitutes its state at any point in time. One important component of state include its machine state, which is made up of memory (i.e. address space), CPU registers and I/O information (i.e. which file are open).  Special CPU registers include the program counter (i.e. instruction pointer), stack pointer (points to function parameters, address spaces, and local variables), and frame pointer.

## The process API

start here page 29

