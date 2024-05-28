---
title: Difference between CVCS and DVCS
draft: false
tags:
---
Uplink : [[Git]]

## Difference Between

| **CVCS**                                                                                                                             | **DVCS**                                                                                                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| In CVCS, a client need to get local copy of source from server, do the changes and commit those changes to central source on servers | In DVCS each client can have a local branch as well as and have a complete history on it. Client need to push the changes to branch which will then be pushed to server repository. |
| CVCS systems are easy to learn and setup                                                                                             | DVCS system are difficult for beginners. Multiple command needs to be remembered                                                                                                    |
| Working on branches is difficult in CVCS. Developer often faces merge conflict                                                       | Working on branches is easier in DVCS. Developer faces less conflict.                                                                                                               |
| CVCS system do not provide offline access                                                                                            | DVCS system are working fine on offline mode as a client copies the entire repository on their local machine                                                                        |
| CVCS is slow as every command needs to communicate with server                                                                       | DVCS is faster as mostly user deals with local copy without hitting server everytime.                                                                                               |
| If CVCS server is down, developers cannot work                                                                                       | If DVCS server is down. Developers can work using their local copies.                                                                                                               |
