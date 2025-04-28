# Chapter 2 Introduction to Operating Systems

A running program executes instructions.

When a program runs, millions of times each second, the processor fectches instructions from memory, decodes it and executes it until the program completes.

The opreating system is the software that manages the system/hardware correctly and efficiently in an easy to use manner.

The OS does this through a technique called virtualization. The OS provides an interface/API to allow users to tell the OS what to do. Every OS has several hundred system calls  to run programs, access memory, devices, and files.

Because virtualization allows many programs to run concurrently and access their own instructions and data, the OS is also known as a resource manager.

## Virtualizing the CPU

Turning a single CPU into the illusion that the system has a large number of virtual cpus allowing multiple programs to run at once is one of the primary jobs of the operating system.

Policies are the way the operating system decides the priority of which program to run when and how to allocate resources.

## Virtualizing Memory

Physical memory is the actual RAM in the system. Memory is an array of bytes, to read memory one must specify the address to access the data stored there. To write or update memory, one must also specify the data to be written to the address.

Memory is accessed all the time the program is running. A running program keeps all of its data structures in memory. Each instruction of the program is stored in memory too, so memory is accesed on each instruction fetch.

Each running program appears to have its own private memory instead of sharing the same physical memory with all other prorams. This is done through an OS technique called virtualizing memory. Each process accesses its own private virtual address space which the OS maps onto the physical memory of the machine. Physical memory is a shared resource that is managed by the OS.

Concurrency - refers to the host of problems that arise and must be addressed when working on many things at once (concurrently) in the same program. Concurrency is how the OS juggles many things at once, first running one process then another.

Threads - a function of a program that runs in the same memory space as other functions, with more than one active at a time. When many threads are working in the same memory space all at once how can we build a correctly working program?  This is problem of concurrency.

## Persistence

System memory like RAM stores values in a volatile manner - when power goes away or the system crashes the data in memory is lost. We need hardware and software to store data persistently.

The hardware comes in the form of input/output (I/O) devices, a hard drive or ssd for example.

The operating system sofware that manages the disk is called the file system. It stores files the user creates on disk. The file system is the part of the OS responsible for managing persistent data.

System calls to save a file include `open()` which opens the file and creates it, `write()` to write data to the file, and `close()` to close the file. These system calls are routed to the file system which handles the requests and returns a error code to the user.

Device drivers are how the OS actually wites to the disk. The OS provides a standard way to access devices through systems calls.

## Design goals

The OS takes physical resources, vitualizes them, handles tricky issues related to concurrency, and stores files persistently and safe to access over the long term.

Finding the right tradeoffs in these areas is the key to building an operating system. One of the goals in designing and implementing an operating system is to provide high performance and minimize overhead. Overhead comes in many forms - extra time, more instructions, extra space in memory or disk.

Isolation is one of the main principles of operating systems. Isolating processes from one another and the operating system in general and is the key to protection.

Code that runs on behalf of the OS is special. It has control of devices and should be treated differently than normal application code.

### System calls

The idea of system calls is to provide a special pair of hardware instructions and hardware state to make a controlled process. The key differnece between a system call and a procedure call is that a system call transfers control (i.e. jumps) into the kernel space while simlutaneously rasing the hardware privilege level. User applications run in user mode, which means the hardware restricts what applications can do - an application typically cannot initiate an I/O request to disk.  When a system call is initiated a special hardware instruction called a **trap**.  The hardware transfers control to a pre-specified trap hanlder and raises the privlege level to kernel model. In kernel mode the OS has full access to the hardware and can do things like I/O, network requests, or issue more memory to a program. When the OS is done with the request, it passes control back to the user via return from trap instructions that revert to user mode and pass control back to where the applcation left off.

## Multiprogramming

Multiprogramming is a way to make better use of machine resources. Insteafd of just running one job at a time, the OS would load multiple jobs into memory and switch rapidly between them, improving CPU utilization. Switching is important because I/O devices are slow and having a program wait on CPU while an I/O request was serviced wasted prescious CPU time.  Memory protection keeps programs from accessing one anothers memory. Concurrency issues while jobs were waiting and resuming in the presence of interrupts led to developments in scheduling.
