---
title: Introduction to Git
draft: false
tags:
---
Uplink : [[Git]]

To understand Git we have to first Understand these two terms :
- [[01 Introduction to Git#^03e9db|Centralized Version Control System (CVCS)]]
- [[01 Introduction to Git#^528c8b|Distributed Version Control System (DVCS)]]

---
## Centralized Version Control System (CVCS)

- It is a Remote server placed somewhere to store the code of multiple users/coders/programmers.
- It is useful if multiple employees are working on a same project
- It was introduced before Git was released
- ![[CVCS.svg]]
- Here all files are stored in a repository which we can call a storage or folder 
- And Commit means to save or we can say to update the code
- Everything is stored on the server 
- But it has some drawbacks like :
	- It is not locally available, meaning you always need to be connected to the internet to perform any action
	- Since Everything is centralized, if local server gets failed, you will lose entire data. e.g. SVN tool.

---
## Distributed Version Control System (DVCS)

- In Distributed Version Control System, every contributor has a local copy or "clone" of the main repository. 
- i.e. everyone maintains a local repository of their own which contains all the files & metadata present in their directory
- ![[DVCS.svg]]
- Even if the remote server or centralized server gets crashed it will not effect the local repo
- Git is a example of DVCS
- It Doesn't need any internet connection
- Git was introduced in 2005 and was made by **Linus Torvalds** who made [[021-1-3 What is Linux|Linux]]