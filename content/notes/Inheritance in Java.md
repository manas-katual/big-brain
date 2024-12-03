---
title: Inheritance in Java
draft: false
tags:
---
Uplink : [[Java]]

- Java me 2 tarah ke class ke hote hai parent and child
- Aur inheritance ka matlab parent class ke members ko child class access kar sakta hai
- Parent ko Super aur Base bhi bolte hai and Child ko Sub aur derived bhi bolte hai
- Java me 3 types ke inheritance hote hai
	- Single
	- Multilevel
	- Hierarchical

#### Example

Single
```java
class A{
	
}
class A extends B{

}
```

Multilevel
```java
class A{

}
class B extends A{

}
class C extends B{

}
```

Hierarchical
```java
class Samsung{

}
class Oppo extends Samsung{

}
class Vivo extends Samsung{

}
```
iske andar ek root yani baap hota hai aur baki sab bacche yani child

Full Example code
```java
class Samsung{
	int x, y;
	void f1(){
		System.out.println("Parent executed");
	}
	void f2(){

	}
	//Samsung(){
	//	System.out.println("Parent's constructor executed");
	//}
}

class Oppo extends Samsung{
	int z;
	void f3(){
		System.out.println("Child 1 executed with single inheritance type");
	}
}

class Vivo extends Samsung{
	void f4(){
		System.out.println("Child 2 executed with multilevel inheritance type");
	}
}

class Inherit{
	public static void main(String args[]){
		Vivo x1 = new Vivo();
		x1.f1();
		//x1.f3();
	}
}

```

One more important thing i.e. **Constructor using Inheritance & SUPER Function**
```java
class Nokia1{
	int x, y;
	void f1(){
	}
}

class Nokia2 extends Nokia1{
	int z;
	void f2(){
	}
	Nokia2(){
		super(); // ye automatic banta hai
		System.out.println("Child constructor executed");
	}
}

class Inherit{
	public static void main(String args[]){
		Nokia2 n1 = new Nokia2(); // jab hum yaha object banate hai to child ke constructor me automatic `super();` function create ho jata hai jo invisible rehta hai same like constructor agar hum banayenge to compiler nahi banayega and vice versa
	}
}
```