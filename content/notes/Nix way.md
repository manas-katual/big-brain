---
title: Nix way
draft: false
tags:
---
Uplink : [[Custom-Rom]]

First install nix package manager
```bash
curl --proto '=https' --tlsv1.2 -sSf -L https://install.determinate.systems/nix | sh -s -- install
```
then run `nix --help` to check if it is installed

This command will make a bin directory and set the PATH variable
```bash
mkdir ~/bin && PATH=~/bin:$PATH && cd ~/bin && curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo && chmod a+x ~/bin/repo && cd
```

clone this in your home directory
```bash
git clone https://gist.github.com/8d11dc53e4110c96f62c3b0ffc1aa18a.git ~/shell.nix
```

now setup build environment by running this
```bash
cd ~/ && nix-shell
```

after this follow the instruction of your favorite custom rom to build it. 