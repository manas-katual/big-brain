---
title: Classes & Objects in C++
draft: false
tags:
---
Uplink : [[C++]]

In C programming there is a concept called `struct` it is also available in C++, classes are almost similar to that with some differences.

The main difference between `struct` of C and C++ is
- In C we cannot create functions inside `struct` but in C++ we can create functions inside `struct`

whenever we make structure we can access all it's content(variables/functions) in `main()` it is public
```c++
struct Nokia {
	int speaker;
	char a;
	int radio;
	void func1()
	{
		cout<<"Hello";
	}
	void someFunc()
	{
		cout<<"Bye";
	}
};
main()
{
	Nokia n1;
	n1.speaker = 24;
	n1.a = 'T';
	n1.func1();
}
```

but in `class` we cannot access all the contents(variables/functions) as by default all contents(variables/functions) inside `class` are private
```c++
class Nokia {
	int speaker;
	char a;
	int radio;
};
main()
{
	Nokia n1;
	n1.speaker = 24;
	n1.a = 'T';
}
```

![[Classes & Objects C++.svg]]