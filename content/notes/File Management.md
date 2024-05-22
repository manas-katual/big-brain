---
title: File Management
draft: false
tags:
---
Uplink : [[RHCSA]]

# Linux File Management 
## Linux File System

  
1. **/** &rarr;
    - It is the root directory of Linux file system. It is the mount point of the system partition. All other files & directories are always **"/"** directory.
    - In Linux everything starts with **"/"** directory and end in **"/"** directory.
2. **/boot** &rarr;
    - It contains all the boot files required to start the OS.
    - When we power on the server OS cannot start automatically.
    - OS cannot start automatically no matter what.
    - First the boot files are loaded and after that the operating system boots.
    - It is advisable not to do anything with **/boot** file or store any private data unless we are given task
3. **/dev** &rarr;
    - It contains all the device driver files needed by hardware devices. The OS cannot use hardware devices. The OS cannot use hardware directly. Device driver is a link between the OS and hardware.
    - Every OS cannot directly talk to the devices like mouse, keyboard, Network, cd-rom, Hard drive it needs device drivers.
    - First OS
4. **/lib** &rarr;
	- It contains all the library files. They are known as kernel modules in Linux. File extension of kernel modules are ".ko" ".so"
	- In every OS there are 2 space kernel space & user space "/lib" is the kernel space and every other directories are user space
	- In Linux we have a dedicated directory for kernel it is called /lib
5. **/usr** &rarr;
	- It contains all the commands and some optional config files.
	- Commands in Linux are of 2 types.
	- BIN (binary) - binaries stored in /usr/bin, can be used by all users
	- SBIN (superbinary) - binaries stored in /usr/sbin, can only be used by root
	- /usr doesn't contain files directly it contains sub directories 
	- User will give the command through shell to the user space and then it will search the commands in /usr/bin or /usr/sbin and it will pass the message to kernel space. Execution will happen at the kernel space and it will then show the output/error to the user space
	- ![[Operating_System_v3.svg]]
1. **/var** &rarr;
    - It contains all the logs and messages related to system, hardware and applications.
    - Its structure is like
    - ==Diagram space==
2. **/proc** &rarr;
    - It is a mount point to ram. Information of all the running process is stored in this directory.
    - It is task manager of Linux.
3. **/etc** &rarr;
    - It contains all the config files of applications and system. Almost all type of administrative task in Linux is done from this directory.
    - Linux Administrators spend most of the time in **/etc**
    - Every directories configuration is stored in **/etc**
    - For e.g. _/boot, /proc, /var etc._
4. **/home** &rarr;
    - It contains the home directory of all local users  
        e.g. → /home/ganesh  
        → /home/ramesh
    - /home is like a building and Ganesh & Ramesh have their seperate Room inside home
    - They cannot enter in other rooms
10. **/root** &rarr;
    - It is the home directory for root user
    - It doesn't come under /home directory
    - root user can access all users directory (it can enter in any other rooms)
    - root is the king of Linux
11. **/tmp** &rarr;
    - It is a public directory where all users can create data.
    - for e.g. ganesh creates a directory in /tmp it will be accessible to Ramesh
    - You can see each others data but you cannot modify it without their permission

---
## Some Basic Commands/Concepts

1. `cd` &rarr; change directory
2. `touch` &rarr; make empty file
3. `mkdir` &rarr; for making directory (folder)
4. `ls` &rarr; list
5. `ls -l` &rarr; long-list (with extra details)
6. `ls -la` &rarr; long-list all 
7. `ls -lh` &rarr; long-list human readable 
8. `ls -lha` &rarr; long-list human readable all
9. `ls -lhd` &rarr; long-list of directory itself
10. `pwd` &rarr; print working directory


- Linux is case sensitive
- e.g. If we create `ABC` and we create `abc` it will be both different file or directory
- Linux is space sensitive
- spaces are not allowed in Linux while creating a file/folder
- There is no concept of file extensions in Linux
	- e.g. (.mp3, .txt, .pdf)
- `file` command is used to know file type or format


>[!Note]
A user will always login into his home directory
<u>example :</u> 
&rarr; ganesh will login into `/home/ganesh`
&rarr; mahesh will login into `/home/mahesh`
&rarr; root will login to `/root`

 ==More commands with images coming soon==

---
## Absolute Path

- Complete path from current location to reach a destination file or directory is called absolute path

![[Absolute_Path.svg]]

`. dot`  &rarr; it represents current directory
`.. double dot` &rarr; it represents previous directory
`~ tilda` &rarr; it represents user's home directory
`$ dollar` &rarr; it means normal user
`# hash` &rarr; it means root user

- In Linux if we want to change our directory we start from `/` 
- for e.g. If we want to go to conf directory the command will be `/etc/httpd/conf` (refer to above diagram)
- If we are in a directory `/etc` and we want to go to totally different directory `/usr/local/sbin` then we have to give its absolute path e.g. `cd /usr/local/sbin`
- if we want to go to previous directory (one step back) the command will be `cd ..` if we want to go 2 step back then it will be `cd ../..`

- root user (home directory) :-
	`/root/Desktop`
	OR
	`/~/Desktop`

If we want to go to our home directory we simply press ~(Tilda) symbol in keyboard


### Commands

1. `ls /usr` &rarr; it will show content in /usr
2. `ls /usr /home /etc/default` &rarr; It will show contents in 3 diffrent paths
3. `mkdir /usr/d1` &rarr; It will create directory in /usr
4. `mkdir -p /linux/distros/redhat` &rarr; It will create a path with directories *'here -p stands for parent directory'*
5. `mkdir /linux/distros/{centos,ubuntu,kali,Arch,Gentoo}` &rarr; It will create subdirectories inside /linux/distros 
6. `cp /usr1.txt /linux/distros/redhat` &rarr; it will copy the file 
7. `cp -r /usr/d1 /linux/distros/redhat` &rarr; it will copy subdirectories and its content
8. `mv /usr`
9. `rm `
10. `rm -f`
11. `rm -rf`

---
## Search Commands

To search any file or folder on Linux commands are as follows

### Find
- find command is used to search data in bulk
- various criteria to search data
- name pattern, file size, type, creator
- no database file
- search data in real directory structure
- we need to provide a target directory

### locate 
- By using this command we can locate any file or folder absolute path
- It's database is inside `/var/lib/mlocate/mlocate.db`
### updatedb  
- It is best practice to update the database of file system before using locate command
### pipline | 
- 2 or more commands to derive a single output It is represented as `|`. ==(example comming soon) ==

---

## Output and Error redirection 

### Output redirection :-

 - another terminal &rarr; to show in another terminal
 - in a file &rarr; to save in a file
 - `/dev/null` (discard the output) &rarr; to do not want to show
 - ">" sign in used to redirect the output

### Error redirection :-

- another terminal
- in a file 
- /dev/null (discard the output)
- "2>" sign is used to redirect the error

### Redirect both (error & output) :-

- "&>" sign is used to redirect the output

### In case of files :-

- "2> & >" will either create a new file or overwrite existing file.
- "2>> & >>" will append the content in the existing file without overwriting it.

==Examples will be comming soon==

---

## Text editor

1. **nano**
2. **vim (vi) most popular text editor in Linux**

### Nano
- Easy to use but not so popular and all shortcuts are show on the screen
- command &rarr; nano filename

### [[021-2-7 Vim Editor#VIM|Vim]] (vi) 
- Most powerful and fastest text editor we need to learn vi
- command &rarr; vim filename
#### Mode
- execution : To perform operation
- insert : to type the data


> [!NOTE] 
> default mode is execution in vim
### sed

- stream line editor
- print the modified data of a file
- make changes in a file

---

## VIM

1. `i` &rarr; enter into insert mode
2. `esc` &rarr; enter into execution mode
3. `esc:w` &rarr; write changes
4. `esc:w` /apple.txt &rarr; write changes with file name
5. `esc:wq` &rarr; write changes and quit the file
6. `esc:wq` /apple.txt &rarr; write changes and quit with the file name
7. `esc:q` &rarr; quit the file
8. `esc:q!` &rarr; quit without saving changes
9. `yy` &rarr; to copy current line
10. `p` &rarr; to paste copied line below current line
11. `10yy` &rarr; copy 10 lines
12. `dd` &rarr; delete current line
13. `10dd` &rarr; delete 10 lines
14. `o` &rarr; open a new line below current line
15. `shift + o` &rarr; open a new line above current line
16. `u` &rarr; undo changes
17. `esc:81` &rarr; go to line 81
18. `esc:$` &rarr; go to last line
19. `esc:set nu` &rarr; see line numbers
20. `esc:set nonu` &rarr; hide line numbers
21. `esc:/word` &rarr; jumb to the number containing word/phrase

---

## Tar Backup

- It is always a best practice to take backup of critical system files and user data to avoid a disaster
- In all Linux flavors we have a data archive utility to backup files and folders into a single archive file
- This utility is called tar
- tar is a data archive manager which easily pack multiple files and folders in a single archive 
- The original files and folders remain as it is, and the new archive file gets created. Hence it is called data backup

### Commands

- Create a data backup archive:
	`# tar cf /data.tar /usr/bin`
	==here, /data.tar is new archive file and /usr/bin is the folder whose backup will be done==
- List data in an archive 
	`# tar tvf /data.tar`
- Extract all data from an archive
	`# tar xf /data.tar`
- Extract selected files from an archive
	`# tar xf /data.tar abc.txt xyz.txt`
	==here, abc.txt and xyz.txt are files that are to b extracted from /data.tar archive==

[[Linux Fundamentals | Prev :]]