[[Linux]]
[[systemd]]


1. Power on -> BIOS (basic input/output system) or UEFI (unified extensible firmware interface) is loaded from disk and executes POST (power on self test).
2. BIOS detects devices connected to the system -> CPU, RAM, storage
3. Boot device is chosen to book the OS, hard drive, network, usb, 
4. BIOS starts the bootloader (GRUB), which starts the kernel
5. When the kernel is ready, system switches to the user space and starts up Systemd init as the first process. Init manages the processes and services, starts other hardware, mounts the file systems, starts desktop
6. Systemd starts default target units
7. Systemd runs startup scripts and configures the environment. 
8. Users receive a login window and system is ready

https://bytebytego.com/guides/linux-boot-process-explained/


![[Pasted image 20260214144812.png]]