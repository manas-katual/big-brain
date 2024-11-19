---
title: While loop in C
draft: false
tags:
---
Uplink : [[C]]

for loop and while loop are same
```c
void main()
{
	int a = 0;
	while(a<5)
	{
		printf("Hello");
		a++;
	}
}
```

there are multiple examples of infinite loop but here is one example
```c
void main()
{
	int a = 1
	while(a!=8)
	{
		printf("Hello");
		a = a+3;
	}
}
```

## Do while

```c
void main()
{
	int a = 0;
	do
	{
		printf("Hello");
		a++;
	}while(a<5);
}
```

while loop and do while loop are almost same but there is one difference
```c
// while loop
void main()
{
	int a = 5
	while(a<5)
	{
		printf("hello");
		a++;
	}
}
```

```c
// do while loop
void main()
{
	int a =5;
	do
	{
		printf("Hello");
		a++;
	}while(a<5);
}
```
this will not print anything in `while loop` but in `do while loop` it will at least print one time