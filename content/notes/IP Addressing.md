---
title: IP Addressing
draft: false
tags:
---
Uplink : [[Networking basics]]

There are 2 types of address one is physical address and other is logical address
Physical address is like someone's name if we ask someone where does luffy stays no one can answer but logical address is like someone's full address like *32, street, lugenford, London* which if we ask this anyone he should be able to tell

![[IP_Addressing.svg]]

## IPv4

- IP stands for Internet Protocol
- It consists of 32 bit logical address 
- 4 octets
- range from 0 - 255
- IP Address = Network ID + Host ID
- ![[IP_Addressing_2.svg]]

Classes

| Class A | 1.0.0.0 - 126.0.0.0       |
| ------- | ------------------------- |
| Class B | 128.0.0.0 - 191.255.0.0   |
| Class C | 192.0.0.0 - 223.255.255.0 |
| Class D | 224 - 239                 |
| Class E | 240 - 255                 |
We only use class A, B and C. Class D is for multicasting. Class E is for Research

if given any random IP address how to tell IP address is of which class
we have to check the 1st octet and tell
e.g. 137.20.20.10 is of class B because 137 the first octet lies in class B

If anyone ask what is Network ID

| Class A | N   | H   | H   | H   |
| ------- | --- | --- | --- | --- |
| Class B | N   | N   | H   | H   |
| Class C | N   | N   | N   | H   |

N - Network - 1 bit
H - Host - 0 bit

e.g. 115.10.0.15 tell its network ID
steps
- first check in which class it belongs
- second check the network table above the network section will remain same and rest will be zero
- like for example if the ip address comes in class A then according to the table above it consists one network and 3 host so the network section will remain same and the host section will become zero
- same goes for class B and class C
- 115.10.0.15 will become 115.0.0.0
- its like the network part remains same and the host part becomes 0 