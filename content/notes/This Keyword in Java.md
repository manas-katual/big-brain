---
title: This Keyword in Java
draft: false
tags:
---
Uplink : [[Java]]

- It is used to avoid name conflicting
- `this` keyword sab function ke andar hota hai jo invisible rehta hai.
- `this` keyword class ka jo variable hota hai usko hi access karta hai


```java
class Example{
	private int x, y;
	void f1(int x, int y){
		this.x = x; // equal to ke pehle wala `x` private int x hai and equal to ke baad wala `x` function parameter wala x hai
		this.y = y; // same for y
	}
	void display(){
		System.out.println(x);
		System.out.println(y);
	}
}

class ThisK{
	public static void main(String args[]){
		Example e1 = new Example();
		e1.f1(55, 66);
		e1.display();
	}
}
```

### polymorphism

jab aise same naam wale function rahenge compiler object ke according function ko chalata hai usi ko polymorphism kehte hai
```java
class A{
	void f1(){
	}
	void f1(int q){
	}
	void f1(int p, int x){
	}
}

class Example{
	A a1 = new A();
	a1.fun1();
	a1.fun1(6);
}
```
### function overloading

agar kisi ek class me ya dusre class me same naam ke multiple function bante with different arguments use function overloading bolte hai
```java
class A{
	void f1(){
	}
	void f1(int q){
	}
	void f1(int p, int x){
	}
}
```

### function overriding

agar same naam ke function alag alag class me bante hai with same arguments to use function overriding bolte hai
```java
class A{
	void f1(int q){
	}
}
class B{
	void f1(int q){
	}
}
```

> [!NOTE]
> Function overriding same class me nahi ban sakta
