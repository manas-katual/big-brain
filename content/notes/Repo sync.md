---
title: Repo sync
draft: false
tags:
---
Uplink : [[Custom-Rom]]

- we will build custom rom of lineageOS same follows for every other custom rom out there
- go to the LineageOS [github](https://github.com/LineageOS) and look for android or manifest repository and follow thier instructions or do this 

To initialize your local repository, use a command like this:
```bash
repo init -u https://github.com/LineageOS/android.git -b lineage-21.0 --git-lfs
```

Then to sync up:
```bash
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags --optimized-fetch --prune
```

