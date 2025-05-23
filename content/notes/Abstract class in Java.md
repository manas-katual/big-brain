---
title: Abstract class in Java
draft: false
tags:
---
Uplink : [[Java]]

- kisi bhi class ke aage agar hum `abstract` keyword lagate hai to us class ka hum `object` nahi bana sakte error ayega.
- agar hum kisi normal class me kisi function ke aage `abstract` keyword lagate hai to us class ko bhi hume `abstract` bana na padega.
- kya abstract class ke andar constructor banta hai ? ha banta hai 

```java
abstract class Demo{
	int x, y;
	abstract void f1();
	Demo(){
		System.out.println("Parent's contructor");
	}
}

class Demo1 extends Demo{
	int z;
	void f1(){
	}
	Demo1(){
		System.out.println("Child's Constructor");
	}
}

class Abs{
	public static void main(String args[]){
		Demo1 d1 = new Demo1();
	}
}
```

- is example me jab humne child ka object banaya 
- tab internally pehle child ka contructor chala quiki humne child ka object banaya hai lekin child ke contructor me by default `super();` function likha hua rehta hai 
- jo invisible rehta hai (wo `super();` function ka matlab hi hai jao jaake parent ko chala ke aao ) 
- tab wo upar jaake child ka constructor chalata hai and then apna khudka constructor chalata hai 