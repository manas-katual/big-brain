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
This code will give error because humne jab function banaya wo static function nahi hai aur hum static context ke andar non-static function nahi call kar sakte quki main function static hai.

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

class object1{
	public static void main(String []args){
		System.out.println("Bye");
		Mahesh m1 = new Mahesh(); // this is syntax of java to create a object
		m1.x = 51;
		System.out.println(m1.y);
	}
}
```