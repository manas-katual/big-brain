---
title: for loop in C
draft: false
tags:
---
Uplink : [[C]]

## Iterative statement

for loop is a iterative statement

```c
void main()
{
	int i,j;
	for(i=0;i<5;i++)
	{
		printf("A");
	}
}
```

nested for loop
```c
void main()
{
	int i, j;
	for(i=0;i<5;i++)
	{
		printf("A");
		for(j=0;j<=7;j++)
		{
			printf("B");
		}
	}
}
```

Write a C program to calculate table
```c
void main()
{
	int i, n;
	int a[10];
	printf("Enter a number: ");
	scanf("%d", &n);
	for(i=0; i<=10; i++)
	{
		a[i] = n*i;
		printf("%d\n", a[i]);
	}
}
```