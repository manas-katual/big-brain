---
title: printf and scanf in C
draft: false
tags:
---
Uplink : [[C]]

## printf

whenever we write a program in c we start with `main()`
```c
main()
{
	printf("Hello World");
}
```
this is a simple program which print hello world on screen we have to always end with `;` it is like `full stop (.)` we use in English language 

## data types

- data types in c are int, float, char, etc. 
- we can also call it memory in simple words. 
- It basically creates small memory in our ram so we can use later

```c
main()
{
	int x;
	float y;
	char z = 'G' ;
	x = 6;
	y = 8.45;

	printf("%i\n", x);
	printf("%f\n", y);
	printf("%c", z);

	getchar();
}
```

- int is used to store integer
- float is used to store decimals
- char is used to store a character we can only use single character in single inverted comma.
- x, y, z is variables
- here `%i` stands for **"integer"**,
- `%f` for **"float"**, 
- `%c` for **"character"** 
- we can also use `%d` for **"decimal"** which we can use in place of `%i`
- and there is one more `%u` for **"unsigned integer"** which only prints +ve numbers
- `%i` `%f` `%c` `%d` `%u` are called format specifier which is non printable character 
- `getchar()` is optional it is only used so that program doesn't end until we press any key from keyboard. It's name is itself "get character" 

==diagram==

To check data type is of how many byte
```c
printf("%d",sizeof(int));
printf("%d",sizeof(char));
```

let's write a program to add numbers
```c
main()
{
	int a, b, c;
	a = 4;
	b = 5;
	c = a + b;
	printf("Addition is %d", c);
}
```

## scanf

scanf tells users to enter any number/input and stores in memory/variable
let's understand with an example

Write a c program to add 2 numbers
```c
main()
{
	int x, y, z;
	printf("Enter 2 number: ");
	scanf("%d", &x);
	scanf("%d", &y);
	z = x + y;
	printf("Addition is %d", z);
}
```