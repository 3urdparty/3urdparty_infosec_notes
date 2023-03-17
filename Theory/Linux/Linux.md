- [ ] Format this 📅 2023-03-16 

## Linux Principles
Linux follows five core principles:
| Principle | Description |
| --------- | ----------- |
| Everything is a file | 	All configuration files for the various services running on the Linux operating system are stored in one or more text files. |
Small, single-purpose programs 	Linux offers many different tools that we will work with, which can be combined to work together.
Ability to chain programs together to perform complex tasks 	The integration and combination of different tools enable us to carry out many large and complex tasks, such as processing or filtering specific data results.
Avoid captive user interfaces 	Linux is designed to work mainly with the shell (or terminal), which gives the user greater control over the operating system.
Configuration data stored in a text file 	An example of such a file is the /etc/passwd file, which stores all users registered on the system.

## Components

| Component | Description |
| --------- | ----------- |
| Bootloader |	A piece of code that runs to guide the booting process to start the operating system. Parrot Linux uses the GRUB Bootloader. |
OS Kernel 	The kernel is the main component of an operating system. It manages the resources for system's I/O devices at the hardware level.
Daemons 	Background services are called "daemons" in Linux. Their purpose is to ensure that key functions such as scheduling, printing, and multimedia are working correctly. These small programs load after we booted or log into the computer.
OS Shell 	The operating system shell or the command language interpreter (also known as the command line) is the interface between the OS and the user. This interface allows the user to tell the OS what to do. The most commonly used shells are Bash, Tcsh/Csh, Ksh, Zsh, and Fish.
Graphics server 	This provides a graphical sub-system (server) called "X" or "X-server" that allows graphical programs to run locally or remotely on the X-windowing system.
Window Manager 	Also known as a graphical user interface (GUI). There are many options, including GNOME, KDE, MATE, Unity, and Cinnamon. A desktop environment usually has several applications, including file and web browsers. These allow the user to access and manage the essential and frequently accessed features and services of an operating system.
Utilities 	Applications or utilities are programs that perform particular functions for the user or another program.

## Linux Architecture
| Layer | 	Description|
Hardware 	Peripheral devices such as the system's RAM, hard drive, CPU, and others.
Kernel 	The core of the Linux operating system whose function is to virtualize and control common computer hardware resources like CPU, allocated memory, accessed data, and others. The kernel gives each process its own virtual resources and prevents/mitigates conflicts between different processes.
Shell 	A command-line interface (CLI), also known as a shell that a user can enter commands into to execute the kernel's functions.
System Utility 	Makes available to the user all of the operating system's functionality.

## Important Directories
![[Pasted image 20230316140925.png]]

| Path | Description |
| ---- | ----------- |
| /  |	The top-level directory is the root filesystem and contains all of the files required to boot the operating system before other filesystems are mounted as well as the files required to boot the other filesystems. After boot, all of the other filesystems are mounted at standard mount points as subdirectories of the root. |
/bin 	Contains essential command binaries.
/boot 	Consists of the static bootloader, kernel executable, and files required to boot the Linux OS.
/dev 	Contains device files to facilitate access to every hardware device attached to the system.
/etc 	Local system configuration files. Configuration files for installed applications may be saved here as well.
/home 	Each user on the system has a subdirectory here for storage.
/lib 	Shared library files that are required for system boot.
/media 	External removable media devices such as USB drives are mounted here.
/mnt 	Temporary mount point for regular filesystems.
/opt 	Optional files such as third-party tools can be saved here.
/root 	The home directory for the root user.
/sbin 	This directory contains executables used for system administration (binary system files).
/tmp 	The operating system and many programs use this directory to store temporary files. This directory is generally cleared upon system boot and may be deleted at other times without any warning.
/usr 	Contains executables, libraries, man files, etc.
/var 	This directory contains variable data files such as log files, email in-boxes, web application related files, cron files, and more.

## Default Commands
Command 	Description
whoami 	Displays current username.
id 	Returns users identity
hostname 	Sets or prints the name of current host system.
uname 	Prints basic information about the operating system name and system hardware.
pwd 	Returns working directory name.
ifconfig 	The ifconfig utility is used to assign or to view an address to a network interface and/or configure network interface parameters.
ip 	Ip is a utility to show or manipulate routing, network devices, interfaces and tunnels.
netstat 	Shows network status.
ss 	Another utility to investigate sockets.
ps 	Shows process status.
who 	Displays who is logged in.
env 	Prints environment or sets and executes command.
lsblk 	Lists block devices.
lsusb 	Lists USB devices
lsof 	Lists opened files.
lspci 	Lists PCI devices.

## File details
```bash
drwxr-xr-x 2 cry0l1t3 htbacademy 4096 Nov 13 17:34 Videos
```

| Column  Content | Description          |
| --------------- | -------------------- |
| drwxr-xr-x      | Type and permissions |
2 	Number of hard links to the file/directory
cry0l1t3 	Owner of the file/directory
htbacademy 	Group owner of the file/directory
4096 	Size of the file or the number of blocks used to store the directory information
Nov 13 17:37 	Date and time
Desktop 	Directory name

## Linux Package Managers
- [[dpgk]] - for debian packages
- [[apt]] - high-level command-line interface for package management
- [[aptitude]] - friendly alternative to [[dpgk]]
- [[snap]] - for snap packages, utilities for cloud, servers, desktop and internet of things
- [[gem]] - front-end to [[RubyGems]], standard PM for [[Ruby]]
- [[pip]] - PM for python packages
- [[git]]

## Service and process Management
`deamons` are servicecs that run in the background without any user interaction, signified by the `d` at the end of a program name (`sshd`, `systemd`)

>[!INFO] Each process has an ID (`PID`) which can be viewed in `/proc/`

Some examples:
- [[systemd]] - **Init process** and has PID 1, since it starts first, takes care of starting and stopping other services
