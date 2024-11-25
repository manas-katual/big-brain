---
title: Accessing private variables in C++
draft: false
tags:
---
Uplink : [[C++]]

how to access private variables in `class`. we can't access private variables but we can do something like this access the private variables with the help of functions

```c++
#include<iostream>
#include<conio.h>
using namespace std;

class Example
{
    int x, y;

public:
    void setData(int p, int q)
    {
        x = p;
        y = q;
    }

	void display()
    {
        cout<<x<<" "<<y<<endl;
    }
};

int main()
{
    Example e1, e2;
    e1.setData(2, 3);
    e1.display();

    e2.setData(1, 4);
    e2.display();


	getch();
}
```

ek `static` naam ka keyword bhi hota hai jo hum class ke andar static member variable/function create karne ke liye use karte hai `static` member variable/function hum jab bhi banayenge wo apne aap memory turant ban jaati hai hume usko banane ki jarurat nahi padti

```c++
class Demo
{
	int a;
	int b;
	int c;
	// this are normal instance member variables which we can call as object member variables
	static int z; // this is a static member variable
};

int Demo::w; // agar koi class hi nahi banaya hai to static ko aise use karna hoga 

int main()
{
	Demo d1, d2; // jab tak hum ye nahi banate tab tak object nahi banta lekin static ke case me hum jab usko upar class me banate hai wo tabhi ban jata hai
	d1.z = 8;
	d2.z = 17; // ye upar wale 8 ko replace kardega
}
```