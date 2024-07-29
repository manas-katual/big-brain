---
title: Functions
draft: false
tags:
---
Uplink : [[C]]

- If we see brackets after any word considered it as a function like `printf()` `main()`.
- Function is a piece of code. 
- There are 2 types of function 
	- predefined function 
	- user defined function. 
- Predefined are already defined we just use them like `printf()` it is a predefined function and user defined function is something that we users defined or you can say create like for example `amit()`. 
- There are 2 types of User defined functions 
	- call by value/pass by value 
	- call by reference.
- We make function so that we can reuse a code multiple times.

Let's make a simple function that print's `hello amit` when we call that

```c
#include <stdio.h>

void amit()
{
	printf("Hello amit");
}

void main()
{
	amit();
}
```

Let's make a function that adds 2 numbers

```c
#include <stdio.h>

add()
{
	int a, b, c;
	printf("Enter 2 Numbers: ");
	scanf("%d %d", &a, &b);
	c = a + b;
	printf("Addition is %d", c);
}

void main()
{
	add();
}
```

Other ways to create same function

```c
#include <stdio.h>

void add(int a, int b) // formal argument // function definition
{
	int c;
	c = a + b;
	printf("Addition is %d", c);
}

void main()
{
	int x, y;
	printf("Enter 2 Numbers: ");
	scanf("%d %d", &x, &y);
	add(x, y); // actual argument // function calling
}
```

another way

```c
#include <stdio.h>

int add(int a, int b) // formal argument // function definition
{
	int c;
	c = a + b;
	return c;
}

void main()
{
	int x, y, p;
	printf("Enter 2 Numbers: ");
	scanf("%d %d", &x, &y);
	p = add(x, y); // actual argument // function calling
	printf("Addition is %d", p);
}
```