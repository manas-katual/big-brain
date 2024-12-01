---
title: Classes & objects in Java
draft: false
tags:
---
Uplink : [[Java]]


> [!NOTE]
> Hum object naam ka class nahi bana sakte quki wo already predefined class hai

```java
class Object1{
	void fun1(){
		System.out.println("A");
	}
	void fun2(){
		System.out.println("B");
	}
	public static void main(String []args){
		System.out.println("C");
		fun1();
		fun2();
	}
}
```
This code will give error because humne jab function banaya wo static function nahi hai aur hum static context(main) ke andar non-static function nahi call kar sakte quki main function static hai.

To hame function ko static bana na padega is tarah
```java
class Object1{
	static void fun1(){
		System.out.println("A");
	}
	static void fun2(){
		System.out.println("B");
	}
	public static void main(String [] args){
		System.out.println("C");
		fun1();
		fun2();
	}
}
```
ab ye run hoga bina kisi error ke

Hum same chij alag class bana ke bhi kar sakte hai
```java
class Mahesh{
	static void fun1(){
		System.out.println("A");
	}
	static void fun2(){
		System.out.println("B");
	}
}

class Object1{
	public static void main(String []args){
		System.out.println("C");
// bas hume class ka naam phir dot(.) laga ke function call karna hai
		Mahesh.fun1(); 
		Mahesh.fun2();
	}
}
```

How to create private class with private members
```java
class Mahesh{
// agar kisi class ke andar ke variable ko private karna hai to bas uske aage private likhdo 
	int x; // instance(object) member variable
	private int y;
	static void fun1() // instance(object) member function
	{ 
		System.out.println("Hello");
	}
	static void fun2(){
		System.out.println("A");
	}
}

class Object1{
	public static void main(String []args){
		System.out.println("Bye");
		Mahesh m1 = new Mahesh(); // this is syntax of java to create a object
		m1.x = 51;
		System.out.println(m1.y);
	}
}
```

How to access private member variable ?
--> hum kisi bhi private member ko access karne ke liye usi same class me ek function banake niche function ko call kar sakte hai and we can access by creating both static member or by simply creating a object.
```java
class A{
	int x;
	private static int y;
	void fun1(){
		y = 54;
	}
	void fun2(){
		System.out.println(y);
	}
}

class Demo{
	public static void main(String [] args){
		A a1 = new A();
		a1.fun1();
	}
}
```


Tricky code
```java
class A{
	int x;
	private static int y;
	void fun1(){
		y = 54;
	}
	void fun2(){
		System.out.println(y);
	}
	void fun3(){
		y = 45;
	}
}

class Demo{
	public static void main(String [] args){
		A a1 = new A();
		A a2 = new A();
		a1.fun1();
		a2.fun3();
		a1.fun2();
	}
}
```
yaha pe pehle `a1.fun1` ko call kiya jaha pe `y = 54` tha then `a2.fun3` ko call jo ki `y = 45` hogaya  agar hum `a1.fun2` ko call karenge to kya print hona chahiye 
--> yaha pe `45` print hoga quki humne jab `a2.fun3` ko call kiya to `y` ke andar jo `54` tha wo `45` se replace hogaya quki hum jiske aage `static` laga dete hai to wo turant create ho jata hai