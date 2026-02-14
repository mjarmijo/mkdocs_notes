[[Linux]]
# What happens when you press CRTL^C?

When you press Ctrl-C on your local machine, the kernel sends a SIGINT signal (Signal interrupt)  to the foreground process group of the terminal. The terminal driver is responsible for translating key presses into signals and passing them to the correct process group. The default action for SIGINT is to terminate the process, but the process can catch the signal and handle it in a custom way.

When you press Ctrl-C in a terminal, the terminal emulator writes an ASCII character (^C) to the master device. The kernel translates that into sending a SIGINT signal to the foreground process group with the corresponding controlling terminal.  This is actually a default terminal setting. You can run `stty -a` and see that the default is `intr = ^C`;, meaning ^C or ETX is the "SIGINT" character.

```bash line-numbers highlight=3
linux-joe@x1:$ stty -a
speed 38400 baud; rows 24; columns 80; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = <undef>;
eol2 = <undef>; swtch = <undef>; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R;...
```

A more complex example would be how Ctrl-C works through an interactive SSH session. Interactive SSH sessions allocate a pty on the server side. The client side pty is set to raw mode, meaning that the client side kernel will not translate ETX into SIGINT. Instead, the client side kernel passes the ETX along to the slave. In this case, the ssh client process takes that ETX and passes it along to the server sshd process. If the server sshd pty is not in raw mode, then the server's kernel will translate that ETX into a SIGINT to its foreground process group. This is how Ctrl-C sends SIGINT to the process running on the server instead of killing your client side SSH and leaving you hanging.

## Components

### Signals

Signals are a protocol for interrupting and closing programs from the outside. There are a few different types of signals, and they all do different things.

Some signals, like `SIGKILL` and `SIGSTOP`, cannot be caught or ignored by the program. They will always kill or stop the program.

Other signals can be caught by the program and handled in a custom way. For example, Ctrl+C in the terminal almost always sends SIGINT, however, a program can catch `SIGINT` and do something other than exit when it receives that signal.

### terminal - This needs editing

what is a pty? A pty is a pseudo-terminal. It is a pair of devices that provide a bidirectional communication channel. One device is the master, and the other is the slave. The master device is responsible for translating key presses into signals and passing them to the slave device. The slave device is responsible for reading key presses and writing output.

When you run a program in a terminal, the terminal emulator creates a pty pair and runs the program with the slave device as its controlling terminal. The terminal emulator then reads key presses from the master device and writes them to the slave device. The program reads key presses from the slave device and writes output to the master device. The terminal emulator reads output from the master device and displays it on the screen.
