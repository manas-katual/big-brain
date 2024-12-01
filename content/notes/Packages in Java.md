---
title: Packages in Java
draft: false
tags:
---
Uplink : [[Java]]

packages matlab simply folders hota hai java me uske andar bhot saare files hote hai jo ek dusre se link hote hai hum khudka bhi package bana sakte hai

```java
package Pack1;
public class Amit{
	private int x;
	private int y;
	public void setValue(int p, int q){
		x = p;
		y = q;
	}
	public void display(){
		System.out.println(x);
		System.out.println(y);
	}
}
```
iske code andar humne main function nahi likha hai hum main function dusre file me likhenge but ise compile karne ka step thoda alag hai
`javac -d . Amit.java` ye command use hota hai hum jabhi package create karte hai `-d` ka matlab 'directory' and `.` is dot ka matlab 'current directory' 

main function
```java
package Pack2;
import Pack1.*;
class Sumit{
	public static void main(String args[]){
		Amit a1 = new Amit();
		a1.setValue(5, 6);
		a1.display();
	}
}
```
ye main function hai jaha pe hum Amit wale program ko access kar rahe hai

> [!NOTE]
> class and function ko hum public karenge tabhi program compile hoga

Access specifier/modifier
- public
- private
- protected
- default