---
title: Repo sync
draft: false
tags:
---
Uplink : [[Custom-Rom]]

- we will build custom rom of project blaze same follows for every other custom rom out there
- go to the project blaze [github](https://github.com/ProjectBlaze/manifest) and follow thier instructions or do this 

To initialize your local repository, use a command like this:
```bash
repo init --depth=1 -u https://github.com/ProjectBlaze/manifest -b 14
```

Then to sync up:
```bash
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags --optimized-fetch --prune
```

