---
title: Pointers in C
draft: false
tags:
---
Uplink : [[C]]

- jo memory kisi aur memory ka address rakhti hai usko hi pointers kehte hai `&` this is known as address of operator.
- agar kisi memory ke aage `*` hai to usse pointer bolenge.
- agar kisi memory ke aage `**` hai to usse double pointer bolenge.

```c
void amit(int *y)
{
    printf("%d\n",*y);
    *y = 7;
    printf("%d\n",*y);
}

void main()
{
    int z;
    amit(&z);
    printf("%d\n", z);
    getch();
}
```
