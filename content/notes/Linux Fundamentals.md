---
title: Linux Fundamentals
draft: false
tags:
---
 Uplink : [[RHCSA]]
 
## Operating System

- Operating system is the platform between the hardware and software of a computer.
- Computer whether physical or virtual always requires a operating system.
- Operating system has 2 parts : 
	&rarr; User space
	&rarr; Kernel space

![[Operating_System.svg]]

---

## Kernel

- Kernel is the engine of the operating system
- Features of an OS like
	>&rarr; Stability
	&rarr; Reliability
	&rarr; Flexibility
	&rarr; Security
	&rarr; Performance
	&rarr; Hardware Support
	&rarr; Software Support
	&rarr; Architecture
- This all depends on kernel	
- If kernel crashes, the entire OS will crash.



> [!info]
>Any Company when they make Operating system they will first make the kernel and after testing everything they will then build the OS
>

---

## Linux

- Linux was made by **Linus Torvalds in 1991**
- Linux is just a Kernel.
- Linux has only Kernel space and no user space.
- Also, Linux is not a type of Unix.
- Linux is an independent, Unix like Kernel.
- Software companies like Redhat, Suse, Canonical (Ubuntu), etc. create user space on top of Linux Kernel and covert it into an Operating System.
- Redhat Linux is an OS, but Linux is just a Kernel.
- Latest Stable Redhat Linux version is RHEL 9.x with Kernel version 5.x
- Also in smartphones we have Android Operating System with Linux Kernel.

![[Redhat_Chain.svg]]

&rarr; Redhat provides Subscription based product with **24/7 Vendor help/ Support** with Official Update.

&rarr; Linux Distros like centos & Fedora are community based which is not provided by Redhat

&rarr; 80% of Companies use Redhat as their core servers and if they want to reduce some costs they use free Linux based Operating System (not on there core servers)


![[Server_Chain.svg]]

---

## Linux Versions

Kernel development and versions release is handled by **Open Source Community**

![[Linux_versions.svg]]

---
## Storage

- Data is stored physically on hard drives and other storage devices
- We need to access data logically from storage device via operating system 
- Every operating system has a logical access point to access storage devices
- This access points are called mount points
- In windows operating system, mount points are in the form of drive letters

![[Basic_Storage_Concept_1.svg]]

- Linux does not support drive letters
- In Linux empty directories can be used as mount points

![[Basic_Storage_Concept_2.svg]]

- When we install operating system on a hard drive, a default directory structure gets created that contains various system files and can also be used to store user data.
- This default directory structure is called a file system.
- Windows file system start from **C: drive** and contains directories like windows, program files and users
- Since there is no drive letter support in Linux, Linux directory structure starts from a directory called slash directory **"/"** 
- **"/"** is the root directory of Linux file system.
- All other files & directories always fall inside **"/"** directory.
- Various Linux directories that fall directly under **"/"** directory include [[Linux Notes/021 RHCSA/021-2 FIle Management/021-2-1 File System#^3f0f81|boot]], [[Linux Notes/021 RHCSA/021-2 FIle Management/021-2-1 File System#^3a09c4|dev]], [[Linux Notes/021 RHCSA/021-2 FIle Management/021-2-1 File System#^21fa6c|var]], [[Linux Notes/021 RHCSA/021-2 FIle Management/021-2-1 File System#^2a7a7d|usr]], [[Linux Notes/021 RHCSA/021-2 FIle Management/021-2-1 File System#^8accbb|lib]], [[Linux Notes/021 RHCSA/021-2 FIle Management/021-2-1 File System#^c3f9f7|etc]], [[Linux Notes/021 RHCSA/021-2 FIle Management/021-2-1 File System#^5df4b4|proc]], [[Linux Notes/021 RHCSA/021-2 FIle Management/021-2-1 File System#^19ef98|home]], [[Linux Notes/021 RHCSA/021-2 FIle Management/021-2-1 File System#^3ad100|root]], and [[Linux Notes/021 RHCSA/021-2 FIle Management/021-2-1 File System#^3be19b|tmp]]

==for better understanding see below diagram==

![[Basic_Storage_Concept_3.svg]]


---

## Partition Layout

There are two types of partition layout

### Single Partition Layout

- Entire Filesystem is created on a single partition.
- Drawback is that if the partition is corrupted, then all system and user data is lost.
- Suitable for R&D servers

### Multiple Partition Layout

- **"/"** becomes the main system partition and while we have etc, usr, lib, proc, root, tmp and dev directories on itself
- boot, home and var can be declared as mount points of separate partitions

![[Basic_Partition_Layout_1.svg]]

### Swap Partition

- In Linux there is a special partition called swap partition in other words it is virtual memory. It is also known as paging process.
- It provides extra RAM to the system.
- For example if there is 4gb RAM in the system and all the processes are full (RAM is full) then the system (RAM) borrows some space from the storage and it that storage acts as a RAM.
- It is a temporary RAM

![[Basic_Partition_Layout_2.svg]]

---
## Virtualization

![[Virtualization_1.svg]]

### Hypervisor software :- Create Virtual Machine

  There is one physical computer inside that physical computer there can be multiple virtual machines every virtual machines can control different operating system.


![[Virtualization_2.svg]]

---
## Linux Access modes

- **GUI** for desktop purpose
- **CLI** for server purpose 
- From RHEL 7 Redhat introduced 1st ever **"Web UI"** mode  to manage Linux servers In-built cockpit service is used to provide web UI access
- `systemctl enable --now cockpit.socket` command is used to enable cockpit
- Client can use `https://<serverip>:9090` url to access WebUI of server
- We can also download cockpit in another Linux distros

## Terminals

- In Linux login screens are called **Terminals**
- There are two types of terminals :
	> &rarr; **GUI**
	 &rarr; **CLI**
- There are total 6 Local Terminals on RHEL (this applies for all other daily driver linux distro)
- If **Graphics** is **ON** &rarr; **1 GUI & 5 CLI**
- If **Graphics** is **OFF** &rarr; **6 CLI**
- "ctrl + alt + <abbr title="here fn means f1-f6">fn key</abbr>" is used to switch between local terminals
- If Graphics is ON &rarr; f1 for GUI and f2.......f6 CLI
- If Graphics is OFF &rarr; f1......f6 CLI
- Multiple CLI terminals for running parallel tasks

---

## Tmux

**Open Multiple tabs inside a single CLI terminal**
- **tmux application** lets us open multiple tabs inside a single terminal
- **tmux** command is used to start tmux tool
- press and release **'ctrl + b'** and then press  **'c'** to open a new tab in tmux
- press and release *'ctrl + b'* and then tap number to jump on a tab in tmux (e.g 1,2,3)
- After entering into tmux there will be a blue line in bottom inside that blue line the ( * ) asterisk symbol represent current tab and ( - ) symbol represent previous tab.


&rarr; **On GUI terminal**, after login we get **desktop**
&rarr; **On CLI teminal**, after login we get **shell**

Shell is the interactive program that listens to our commands, pass to kernel space and return output/error on screen

**How does a operating system works version 2.0**

First user will give instruction to user space through shell then the shell will pass the instruction to kernel space execution of the instruction will happen in kernel space and after that kernel will give the output/error to user space

**Types of shell :-**
![[Basic_Linux_Terms.svg]]

---

## Data Center

- Data Center is nothing but huge server rooms
- We have to make local (physical) server strong

![[Basic_Linux_Terms_2.svg]]

## Remote Access

 Accessing servers over the network using applications like telnets and SSH

![[Basic_Linux_Terms_2.svg]]

## CLI over GUI mode

- Accessing Linux command-Line on graphical terminal
- Gnome terminal application is used
- Multiple tabs can be opened on a single gnome terminal
- *'ctrl + shift + t'* is used to open gnome tabs.


[[File Management | Next :  File Management >]]