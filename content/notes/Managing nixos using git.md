---
title: Managing nixos using git
draft: false
tags:
---
## Git installation and setup in home manager

> [!NOTE] 
> before following this the directory which is going to be pushed to github should be owned by user not by root

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

Here we also set default branch as main because most of the git hosting providers like github or gitlab use "main" as their default branch but in nixos it is set to "master" so we change it to "main" branch by adding it to the `extraConfig` option

rebuild the system 
if using home-manager as a module `sudo nixos-rebuild switch --flake .`
if using home-manager as a standalone `home-manager switch --flake .`

now after this we can initialize git by doing `git init`

---
## git workflow

### staging

first we have to do `git add *` to add everything inside the folder
to add individual files we have to do something like this `git add configuration.nix` git add and then the file we have to add

### commit

after staging we commit the changes like this `git commit -m "First commit"` -m stands for message we have to give some message what is commit about this is necessary so that we can see later what does this commit says

### push

so to push the changes we have to use a provider like 
- github
- gitlab
- codeberg
- sourcehut

in this we are going to use github
- go to github.com and to settings
- then in the left side bar go to ssh and gpg keys
- then click on new ssh key give it a title and then we have to generate a ssh key
- so go to the terminal and go to your home directory and run `ssh-keygen`
- after entering this will give a default path which is fine press enter and after that give it a password and then it will generate a `.shh` folder inside your home directory 
- in which there will be two files `id.rsa` which is private and `id_rsa.pub` which is public 
- we have to put the public one to the key inside github which is seen by everyone we don't want to put the private key as it is like a password 
- so to achieve that run `cat id_rsa.pub` and copy all the contents in it and paste it in the key section on the github website and click add ssh key

Now we have to create a repository in github but don't add a readme we can add that later
after that we have to copy the ssh git clone link