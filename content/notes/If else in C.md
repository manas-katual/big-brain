---
title: If else in C
draft: false
tags:
---
Uplink : [[C]]

Conditional statements

first let's start with `if` 
```c
void main ()
{
	int x = 7;
	if(x>0)
	{
		printf("It is positive");
	}
}
```

Next `if else`
```c
void main ()
{
	int x = 7;
	if(x>0)
	{
		printf("It is positive");
	}
	else
	{
		print("It is negetavie");
	}
}
```

Next `else if else if`
```c
void main ()
{
	int x = 7;
	if(x>0)
	{
		printf("It is positive");
	}
	else if(x<0)
	{
		print("It is negetavie");
	}
	else if(x==0)
	{
		printf("Neither negetive nor positive");
	}
}
```

Taking input from user
```c
void main ()
{
	int x;
	printf("Enter a number: ");
	scanf("%d", &x);
	if(x>0)
	{
		printf("It is positive");
	}
	else if(x<0)
	{
		print("It is negetavie");
	}
	else if(x==0)
	{
		printf("Neither negetive nor positive");
	}
	else
	{
		printf("Not a valid number");
	}
}
```

Write a program to run maximum of 2 number
```c
void main()
{
	int a,b;
	printf("Enter 2 numbers: ");
	scanf("%d%d", &a, &b);
	if(a>b)
	{
		printf("%d is greater",a);
	}
	else if(b>a)
	{
		printf("%d is greater",b);
	}
	else if(a==b)
	{
		printf("both are equal");
	}
}
```