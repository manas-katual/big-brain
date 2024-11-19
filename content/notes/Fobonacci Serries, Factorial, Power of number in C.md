---
title: Fibonacci Serries, Factorial, Power of number in C
draft: false
tags:
---
Uplink : [[C]]

Let's improve logical thinking

Fibonacci is where you start a number from 0 and 1 and further continue add them `0 1 1 2 3 5 8 ...` 

```c
#include <stdio.h>

void main()
{
	int r, i, a = -1, b = 1, c;
	printf("Enter a range: ");
	scanf("%d", &r);
	for (i = 0; i < r; i++)
	{
		c = a + b;
		printf("%d ", c);
		a = b;
		b = c;
	}
}
```

Calculating Factorial example `4!` it is `4x3x2x1`
```c
#include <stdio.h>

void main()
{
	int x, i, s=1;
	printf("Enter a number: ");
	scanf("%d",&x);
	for(i=1; i<=x; i++)
	{
		s=s*i
	}
	printf("%d", s);
}
```

$$
Calculating \ power \  2^4
$$

```c
#include <stdio.h>

void main()
{
	int x, y, i, s=1;
	printf("Enter a coefficient: ");
	scanf("%d", &x);
	printf("Enter a Power: ");
	scanf("%d", &y);
	for(i=0; i<=y; i++)
	{
		s = s * x;
	}
	printf("Result is %d", s);
}
```