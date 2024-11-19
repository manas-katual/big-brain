---
title: If else in C
draft: false
tags:
---
Uplink : [[C]]

## Macros

when we write something at the starting of the line which are already predefined with hash (`#`) it is called macros
```c
#include

#define

#if 
#else
#endif
```

## Conditional statements

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

Write a program to run maximum of 2 number
```c
void main(){
    int a, b, c;
    printf("Enter 3 numbers: ");
    scanf("%d %d %d",&a, &b, &c);
    if(a>b && a>c){
        printf("%d is greater", a);
    }
    else if(b>a && b>c){
        printf("%d is greater", b);
    }
    else if(c>a && c>b){
        printf("%d is greater", c);
    }
}
```

Write a program to print if a number is even or odd
```c
void main()
{
	int x;
	printf("Enter a number: ");
	scanf("%d", &x);
	if(x%2==0)
	{
		printf("%d is even", x);
	}
	else
	{
		printf("%d is odd", x);
	}
}
```