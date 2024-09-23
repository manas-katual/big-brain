---
title: printf and scanf in C
draft: false
tags:
---
Uplink : [[C]]

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
- `getchar()` is optional it is only used so that program doesn't end until we press any key from keyboard. It's name is itself "get character" 

==diagram==