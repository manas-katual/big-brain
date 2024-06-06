---
title: Install using github
draft: false
tags:
---
Uplink : [[Nixos]]

Run this command to ensure Git & Vim are installed:

```bash
nix-shell -p git vim
```

Clone this repo & enter it:

```bash
git clone https://github.com/manas-katual/nixos-config ~/setup
cd setup
```

- _You should stay in this folder for the rest of the install_

Create the host folder for your machine(s)

```bash
cp -r hosts/default hosts/<your-desired-hostname>
```

**🪧🪧🪧 Edit options.nix 🪧🪧🪧**

Generate your hardware.nix like so:

```bash
nixos-generate-config --show-hardware-config > hosts/<your-desired-hostname>/hardware.nix
```

Run this to enable flakes and install the flake replacing hostname with whatever you put as the hostname:

```bash
NIX_CONFIG="experimental-features = nix-command flakes" 
sudo nixos-rebuild switch --flake .#hostname
```

Now when you want to rebuild the configuration you have access to an alias called flake-rebuild that will rebuild the flake!

Hope you enjoy!