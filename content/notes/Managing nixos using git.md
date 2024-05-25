---
title: Managing nixos using git
draft: false
tags:
---
## Git installation and setup in home manager

> [!NOTE] 
> before following this. The directory which is going to be pushed to github should be owned by user not by root

first add this to your home-manager

```nix
programs.git = {
  enable = true;
  userName = "name";
  userEmail = "example@gmail.com";
  extraConfig = {
    init.defaultBranch = "main";
  };
};
```

Here we also set default branch as "main" because most of the remote git like github or gitlab use "main" as their default branch but in nixos it is set to "master" so we change it to "main" branch by adding it to the `extraConfig` option

**rebuild the system** 
- If using home-manager as a module `sudo nixos-rebuild switch --flake .`
- If using home-manager as a standalone `home-manager switch --flake .`

Now after this we can initialize git by running `git init`

---
### Git workflow

#### Staging

First we have to run `git add *` to add everything inside the folder
to add individual files we have to do something like git add and then the file we have to add
ex. `git add configuration.nix`
#### commit

After staging we commit the changes like this `git commit -m "First commit"` -m stands for message. We have to give some message what is commit about this is necessary so that we can see later what does this commit says

#### push

so to push the changes we have to use a remote like 
- github
- gitlab
- codeberg
- sourcehut
- bitbucket

**In this we are going to use github**

- Go to github.com and to settings
- Then in the left side bar go to **SSH and GPG keys**
- Then click on new ssh key give it a title and then we have to generate a ssh key
- So go to the terminal and go to your home directory and run `ssh-keygen`
- After entering this will give a default path which is fine press enter and after that give it a password and then it will generate a `.ssh` folder inside your home directory 
- In which there will be two files `id.rsa` which is private and `id_rsa.pub` which is public 
- We have to put the public one to the key section inside github which is seen by everyone we don't want to put the private key as it is like a password 
- So to achieve that run `cat id_rsa.pub` and copy all the contents in it and paste it in the key section on the github website and click add ssh key

**Now we have to create a repository in github but don't add a readme file we can add that later**

- After that we have to copy the ssh git clone link remember not to copy the https one 
- Now we have to configure the remote go to the directory that we want to push and in that directory we have to run `git remote add <name> <the cloned link>` most people give name like "origin" if they are pushing it to the one place but if we want to push multiple repos to multiple places we have to give it a name like "github" or "nixos" or whatever you want but make sure to remember it as it will be used whenever you push changes to it
- Now the fun part to push it to the remote we have to run `git push nixos main` here github is the name we defined earlier and also the branch which is main also defined earlier
- After entering first time it will ask for authenticity check say yes and then enter your password we set earlier
- Then if we refresh our github we will see that the repository is created
- Now every time we have to push changes to the github we have follow the same steps
	1. Staging with `git add *` or any particular file we want for example `git add home.nix`
	2. Commit with `git commit -m "any message"`
	3. Push with `git push nixos main` nixos is the name we given earlier and main is the branch we want it to push
	4. Enter the password and it is done

**Now if we by mistake remove all files or our system breaks how to get back to the stage we were before**

- First go to the github and git clone the repo by running `git clone <ssh git link> <folder name>` here in the folder name we can give any name we want so it will not take the default name of the git repo 
- Enter password
- In some cases it changes the git name we defined to something like "origin" we can check by running `git remote` 
- Then to change it we have to first remove it by `git remote rm origin`
- Then add `git remote add nixos <cloned link>`
- Then if we see by running `git remote` now it will be nixos

---
#### Troubleshooting/Fixing errors

- If we make a nix module for example `random.nix` and rebuild the system with `sudo nixos rebuild switch --flake .` or `home-manager switch --flake .` it will give some warning and errors 
- This happens because nix know we have created a git for this folder so first we have to stage it and after that we have to rebuild the system it is not a bug it is a feature so we don't accidently rebuild the system without staging it 
- So do it we have to run `git add random.nix` or `git add *`
- Then rebuild
- And after that `git commit -m "any message"`
- And then push `git push  nixos main`