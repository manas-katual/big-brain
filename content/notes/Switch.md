Link : [[CCNA]]

# Lecture 12


==diagram==
## Switch 

- Switch is an intelligent device as soon as a switch receives a frame on its port it will check MAC address refer MAC table and take forwarding decisions because MAC address is a layer 2 address MAC table is a layer 2 table. Hence switch is a layer 2 device.
- Upon receiving a frame on its port switch will open layer 2 information check destination MAC Address refer MAC table and forward the frame to relevant port only and not to all the other ports whereas Hub forwards it to all the other ports. 
- Switch segments the network Hub extends the network.
- Because switch refers MAC table to take forwarding decisions. Hence MAC table must be populated with MAC Addresses.
- MAC Address can be populated in two ways
	1. Administrator can make static ( manually ) MAC entries in switches MAC table.
	2. Switch can self learn ( dynamically ) MAC Addresses when a frame traverses the switch. 

---
## How will switch learn MAC address

- Switch MAC addresses kaise learn karega.
- switch ek matra aisa device hai jo frame ko pehle puchta hai kaha se aya hai aur phir puchega kaha jaana hai aise puch puch karke wo MAC Address populate karta hai lekin aise puchlene se bohot baar MAC table ka size huge ho sakta hai aur huge MAC table ke 3 drawback hai 
	1. itne saare Addresses ko store karne ke liye storage utilization ekdam high lagega
	2. second problem jab koi ek frame ayega toh lakh addresses ko search karne ke liye switch ka CPU yani processing power ka utilization bhi ekdam high ho jayega aur jab tak search nahi karlega frame ko rok ke rakhna padega
	3. yani ke frame ke forwarding me delay aane lagega aur ye saare problem ko solve karne ke liye 2 solution hai 
		1. MAC table me limit hai total ek MAC table me 4096 Addresses hi store ho sakte hai lekin agar ye table aise log populate karle jo sirf ek hi baar aa rahe hai phir zindagi me kabhi aa nahi rahe to jo har din ayenge uske liye slot bachega nahi to iske liye dusra solution bhi nikala gaya 
		2. jo kehta hai aisi koi entry jo mere switch ne self learn kiya hai ye agar 5 min yani 300 sec tak use nahi hoga to aisi entry ko stale yani badbudar mark kiya jayega aur MAC table se flush kiya jayega

>[!Note]
>Switch kabhi bhi hum Admins ne jo bhi address MAC table me manually daala hai yani static entries remove nahi karega

---

**Operation no. 1** :

When switch receives a broadcast frame on its port then it will create multiple copies of the frame and forward it to all the other ports but not on the same port

**Operation no. 2** :

If sender and receiver are on same port then switch will discard the frames switch switches between the ports not within a ports

**Operation no. 3**

If switch receives a frame whose destination MAC address is not known then the switch will create multiple copies of such frames and forward it to all the other ports. Which means that switch will create multiple copies in two scenarios 
	**Scenario no 1** : When it receives a broadcast frame
	**Scenario no 2** : When it receives a frame whose destination MAC address is not known then it will create multiple copies of such frames and forward it to all the other ports.

**Operation no. 4** :

