---
title: Multi-threading in Java
draft: false
tags:
---
Uplink : [[Java]]

- Multi-threading matlab agar koi ek app hai for example spotify uske andar ek sath alag alag process run hote hai usko multi-threading kehte hai.
- Multi-threading and multiprocessing dono alag hai multi-threading yani ek hi application me multiple programs(process) run hote hai and multi-tasking yani alag alag applications ek sath chalna
- There are 2 ways to implement Multi-threading
	- Using Runnable Interface
	- Using Thread classes

Using Runnable Interface Example
```java
class Process1 implements Runnable {
	public void run(){
		int i;
		for(i=0;i<10;i++){
			System.out.println("Process1: "+i);
		}
	}
}

class Process2 implements Runnable {
	public void run(){
		int i;
		for(i=0;i<10;i++){
			System.out.println("Process2: "+i);
		}
	}
}

class MultiT {
	public static void main(String args [])
	{
		Process1 p1 = new Process1();
		Process2 p2 = new Process2();
		Thread t1 = new Thread(p1);
		Thread t2 = new Thread(p2);
		t1.start();
		t2.start();

	}
}

```

Using Thread class Example