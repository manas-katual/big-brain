---
title: Interface in Java
draft: false
tags:
---
Uplink : [[Java]]

- Interface ki help se bhi hum class bana sakte hai isme bhi abstract jaise hi hum object nhi bana sakte
- Lekin isme thode difference hote hai like Interface me kuch chije by default rehte hai
	- variable - public, static, final
	- function - public, abstract
- jaise ki function by default abstract hote hai so hum function ki body nahi bana sakte to hum jab iski child class banayenge to hume function [[This Keyword in Java#function overriding|overriding]] karna padega parent ke function ko access karne ke liye
- lekin java.ver.8 ke baad se hum Interface me agar function body ke sath bana na chahte hai to hume static function bana na padega
- jab hum ek Interface ki help se dusra Interface banate hai to hume 'extends' likhna padega
- lekin agar ek Interface ki help se dusra class banate hai to 'implements' likhna padega

