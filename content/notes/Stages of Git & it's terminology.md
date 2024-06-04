---
title: Stages of Git & it's terminology
draft: false
tags:
---
Uplink : [[Git]]

## Repository
- Repository is a place where you have all your codes or kind of folder on server.
- It is a kind of folder related to one product.
- Changes are personal to that particular repository.

---
## Server
- It stores all repositories.
- It contains metadata also.

---
## Working directory
- Where you see files physically and do modifications.
- At a time, you can work on Particular branch.
- In other CVCS, developers generally makes modifications and commit there changes directly to the Repository. But git uses a different strategy. Git does not track each and every modified file. Whenever you do commit an operation, git looks for the files present in the staging area. Only those files present in the staging area are considered for commit and not all modified files.
- ![[git workflow.svg]]

---
## Commit
- Store changes in local repository you will get one commit-ID
- It is 40 alpha-numeric characters
- It uses SHA-1 checksum concept
- Even if you change one dot, commit-ID will get change
- It actually helps you to track the changes
- Commit is also known as SHA1 hash

---
## Commit ID/Version ID/ Version
- Reference to identify each change.
- To identify who changed the file

---
## Tags

Tags assign a meaningful name with a specific version in the registry. Once a Tag is Created for a particular save, even if you create a new commit, it will not be updated.

---
## Snapshots
- Represents some data of particular time
- It is always incremental i.e. it stores the changes (appended data) only not entire copy.

---
## Push 

Push operation copies changes from a local repository instance(server) to a remote or central repo. This is used to store the changes permanently into the git repository

---
## Pull

Pull operation copies the changes from a remote repository to a local machine.
The pull operation is used for synchronization between two repo.

---
## Branch

Product is same, So one repository but different task
- Each task has one separate branch
- Finally merges (code) all branches
- useful when you want to work parallelly
- Can create one branch on the basis of another branch
- Default branch is "master".
- File created in workspace will be visible in any of the branch workspace until you commit once you commit, then that file belongs to that particular branch

---
## Advantages of git

- Free and open source
- Fast and small as most of the operations are performed locally, therefore it is fast.
- Security &rarr; git uses a common cryptographic hash function called secure hash function (SHA 1) to name and identify objects within its database
- No need of powerful hardware
- Easier Branching &rarr; If we create a new branch, it will copy all the codes to the new branch

---
## Types of repository

### Bare repositories (Central repo)

- Store and share only
- All central repositories are Bare repo
### Non-bare repositories (Local repo)

- where you can modify the files
- All local repositories are bare-bone repositories