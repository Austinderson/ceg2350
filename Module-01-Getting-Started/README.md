# Module 01 - The foundation

### Why do we use computers?
* Store information (Files)
* Exchange information (Input/Output or I/O)
* Run programs (email clients, web browsers, file browsers, shells, etc.) which
  are typically stored as files

### What is an [Operating System(OS)](https://en.wikipedia.org/wiki/Operating_system "Wikipedia's Operating Systems page")
An Operating System is a collection of software that controls all of the 
hardware and software resources that make up a computer.
![os layers][Operating System between users and hardware]

### What resources make up a [computer](https://en.wikipedia.org/wiki/Computer "Wikipedia's Computer page")?
Computer systems have 3 components:
1. Hardware: Central Processing Unit (CPU), Random-access Memory (RAM),
   keyboard, mouse, and various other input/output (I/O) devices.
2. Software: Operating System and other programs
3. Firmware: A Basic Input/Output System (BIOS) which is sort of a extremely
   bare-bones OS

### Files and Folders
Information is stored on a computer in files.  At the lowest level this
information is encoded in a *bit*.  A bit is a binary digit that can only have 
one of two values, typically represented as either a 0 or 1.

A grouping of bits is called a *byte*.  Most often when we refer to a byte we
are talking about a grouping of *8 bits*.

*Files* are collections of bytes associated with a unique identifier called an
[inode](https://en.wikipedia.org/wiki/Inode "Wikipedia's inode page").  The
inode stores the location on disk of a file, as well as file-system specific
attributes called meta-data.

*Directories* (commonly called Folders) are also files.  Each directory will
have an inode as well as a list of name/inode mappings for all files inside the
directory.  Directories also contain an entry for themselves (typically this
entry is named `.`) and for its parent directory (typically named `..`).

### Programs
Computer programs are special files that are *executable*.  The data stored in
these files includes a set of instructions that are understood by the Operating
System.  Upon exexution (often called running the program) these instructions 
will be loaded into memory and assigned unique identifier (Process ID or PID).

Programs that are not a part of the Operating System are called *applications*.
Applications are programs that the user of a computer must use to interact with
the OS and underlying hardware.  Applications may be bundled *with* and
operating system but are typically not a part *of* the operating system.  For
example, Bash is typically installed by default in most versions of linux, but
Bash itself is not a part of the Linux kernel.

### Executing programs
A computer program is executed by loading its set of instructions into memory 
and assigning a Process ID (PID).  This creates a *process* which in computing
refers to an instance of a program that is being executed.

### [Von Neumann architecture](https://en.wikipedia.org/wiki/Von_Neumann_architecture "Wikipedia: Von Neumann architecture")
The Von Neumann architecture describes a model that is still a very usefull
representation of how computers work today.

![Von Neumann architecture][von neumann arch]

The design architecture is made up of the following:
* A processing unit that contains an arithmetic logic unit and processor registers
* A control unit that contains an instruction register and program counter
* Memory that stores data and instructions
* External mass storage
* Input and output mechanisms

So long as the computer system is powered on, the hardware is constantly reading
an instruction from memory, performs the specified operation on the specified 
data, and then reads another instruction from memory.

##### Operating System as defined by functionality
From [Silbershatz][silbershatz], typical OS functionality includes: 
* To provide an environment for a computer user to execute programs on
  computer hardware in a convenient and efficient manner. 
* To allocate the separate resources of the computer as needed to solve the
  problem given. The allocation process should be as fair and efficient as
  possible. 
* As a control program it serves two major functions: (a) supervision of the
  execution of user programs to prevent errors and improper use of the computer,
  and (b) management of the operation and control of I/O devices."

##### Operating System as a collection of Files
In Linux: 
* /boot/grub/: OS boot loader files.
* /lib/modules: a number of dynamically loadable "modules", which are specially
  linked files that can be incorporated into the running OS.
* /sbin: a number of system programs that the OS can invoke as separate OS helper
  processes.
* /usr/sbin: further system programs. The programs in /sbin are considered
  essential, whereas the one in /usr/sbin are "less" so.
* swap space is located on a separate partition or large file.
* /bin, /usr/bin, ...: not considered part of the OS. The programs in these
  directories are considered simply applications.

##### Operating System as a collection of Processes
Most of the OS stays in RAM (volatile memory)and does not show up in a list of
processes. Consequently, viewing an OS only as a collection of processes is
going to be incomplete.
To see a list of processes running on a computer:
* In Unix use the `ps` program `/usr/ps`
* In Windows use the Task manager `C:\Windows\System32\Taskmgr.exe`


[silbershatz]: http://iips.icci.edu.iq/images/exam/Abraham-Silberschatz-Operating-System-Concepts---9th2012.12.pdf
[os layers]: https://upload.wikimedia.org/wikipedia/commons/e/e1/Operating_system_placement.svg
[von neumann arch]: https://upload.wikimedia.org/wikipedia/commons/e/e5/Von_Neumann_Architecture.svg
