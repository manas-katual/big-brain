---
title: How to commit, push and pull from github
draft: false
tags:
---
Uplink : [[Git]]

## Steps to create a git repo and push

First we have to create a directory and go inside that directory and run
```bash
git init
```

Second create any files or subdirectory inside the directory which we created and write your code

To check the status run
```bash
git status
```
it will show its status

Now to add files to git run this
```bash
git add .
```

Then commit it by doing this
```bash
git commit "any message"
```

after this again check it's status 
```bash
git status
```

Then run this to show it's log
```bash
git log
```

To view what changes we made run this
```bash
git show <commit id>
```
we can copy the commit id from git log command from earlier

Now the final part
To add the remote repository. So that we can access our code from the web or to show anyone our code
we can use any service like github, gitlab and so on.
```bash
git remote add origin <central git url>
```
here `origin` acts like name we give it a name so that we don't always use the git url to push to the central repo we can give any name we want instead of `origin`

Now we push the code to the central repo
```bash
git push -u origin master
```
here `-u` is user this is optional `origin` is the name it acts like the url so that we don't always have to use the url to push the changes, again we have to use the name we defined in the previous command when we added remote repo url and after that it will ask for the username and password of the service which we are using like github or gitlab

> [!NOTE]
> To push to the remote repo we first have to create a repo in github or gitlab
## Steps to pull and push the changes

Create one directory and go inside it
```bash
git init
```

```bash
git remote add origin <central repo url>
```

```bash
git pull -u origin master
```

```bash
git log
```

```bash
git show <commit id>
```

Now add some code in the file

```bash
git status
```

```bash
git add .
```

```bash
git commit -m "any message"
```

```bash
git status
```

```bash
git log
```

```bash
git push -u origin master
```