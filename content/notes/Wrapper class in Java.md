---
title: Wrapper class in Java
draft: false
tags:
---
Uplink : [[Java]]

hum java ko fully object-oriented programming language nahi bolte isse hum almost 100% object-oriented programming language bolte hai quki isme hum normally `int x = 80;` ya phir koi aur data type use kar sakte hai jise hum bina classes ka use kiye bhi kar sakte hai.

isi ko tackle karne ke liye java ne wrapper class introduce kiya jisme hume predefined data types ke predefined classes mil jaate hai like `int` ko `Integer` se `float` ko `Float` se `char` ko `Character` se replace karke use kar sakte hai jaha pe as usual class ka pehla letter humesha [[Classes in Java|capital hota hai]] 

```java
class Wrap {
	public static void main(String [] args)
	{
		int x = Integer.parseInt("123");
		Integer i1 = Integer.valueOf("101110",2); // converting binary to decimal
		int y = i1.intValue();
		System.out.println(x);
		System.out.println(y);
	}
}
```

same for double
```java
class Wrap {
	public static void main(String [] args)
	{
		Double i1 = Double.valueOf("101110",2); // converting binary to decimal
		double y = i1.intValue();
		System.out.println(x);
		System.out.println(y);
	}
}
```