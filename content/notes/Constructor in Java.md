---
title: Constructor in Java
draft: false
tags:
---
Uplink : [[Java]]

- Constructor is a special function, jab hum object banate hai tab chalta hai.
- Constructor use bolte hai, jab class ka naam aur uske andar function ka naam same ho, hume constructor banate time void nahi likhna padta quki wo kuch return nahi karta.
- Sabse jaruri Constructor variable initialization ke liye banate hai hum, taki hume function call na pade aur hum jab object banate hai tab wo chal jaye.
- By default bhi constructor banta hai jo compiler humare liye create karta hai. 
- agar hum constructor banayenge to compiler nahi create karega.
- Constructor ke 2 type hote hai 
	- default - jo compiler banata hai
	- parameterized - Jo user yani hum create karte hai
- Hum multiple constructor bana sakte hai

Example
```java
class Demo{
	int x, y, z;
	Demo(int p, int q){
		x = p;
		y = q;
		System.out.println(x);
		System.out.println(y);
	}
	Demo(){

	}
	Demo(int f){
		x = f;
		System.out.println(x);
	}
}
```