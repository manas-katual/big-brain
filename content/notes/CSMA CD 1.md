Link : [[CCNA]]

# Lecture 8

## Uptime availability

If a network is unavailable for 15 min in a year because of outage, then percentage availability is as follows :

$$
\begin{aligned}

Percentage\,Availability &= \frac{No.\,of\,minutes\,in\,a\,year - Down\,time\,in\,minutes} {No.\,of\,minutes\,in\,a\,year} \times 100 \\ \\

Percentage\,Availability &= \frac{\{(365\times24\times60) - 15\}} {365\times24\times60} \times 100 \\ \\

Percentage\,Availability &= 99.971\,\%

\end{aligned}
$$
$$
\begin{aligned}
Percentage\,Availability\,Required\;99.99\,\% &= \frac{\{(365\times24\times60) - 525.6\}} {(365\times24\times60)} \times 100 \\ \\

Percentage\,Availability &= \frac{(525600 - 525.6)} {525600} \times 100 \\ \\

Percentage\,Availability &= 99.9\,\%

\end{aligned}
$$

If 525600 minutes (365 days) is 100 % then for 99.9 % uptime link can be down only for 525.6 minutes a year ( 8.76 hrs a year )

There are many tools available to calculate down time, cisco routers, and switches provide a tool called "IP SLA" than can be configured on cisco devices to calculate downtime, latency, jitter, drop, etc.

==diagram==

- ICMP echo packet bhejke dekhega kaha pe drop, delay, jitter aata hai 

## Technology

- Technology ka kaam hai communication facilitate karna. 
- Communication karna nahi.
- kisi na kisiko technology use karna padega communication karne ke liye
- Technology khud communication nahi karega
- Technology ke 2 part hote hai Layer 1 and Layer 2
- Layer 1 bole to Hardware
- Layer 2 bole to Software, logics, protocols which drives communication over this hardware
- Layer 1 yani kya aisi koi bhi chij jo physical ya physical in nature hai 
- jo 2 communicating devices ke bichme ek communication ka channel form karta hai isiko hum layer 1 yani hardware kehte hai
- chije jaise ki wire, cable, connector, pinouch, voltages, signal, boosting devices ye sab layer 1 yani hardware hai
- Technology ke 2 type hote ethernet technology and serial technology
- 100 % LAN me hamesha ethernet technology use hota
- aur most of MAN or WAN me serial technology use hota hai lekin kabhi kabar ethernet technology bhi use hosakta hai

---
==diagram==

---

## CSMA/CD

==diagram==

- 2 ya 2 se jyada computers ya communicating devices ek dusre ke sath ek hi medium ke jariye connect ho sakte hai aur communication kar sakte hai jabhi inka man chahe
- as if ye ek democratic world me hai
- lekin har bar communication karne se pehle har pc pehle medium ko sense karega available hai to usko acquire karega phir apna frame medium par daalege aur medium ko release kardega
- jis samay kisi ek pc ka frame wire par hoga us samay wo pc pure medium ka iklota malik hoga jab koi ek pc baat karta hai toh baki sab sunte hai reply kewal wahi deta hai jiske liye frame aya hai baki sab isko discard karte hai 
- quki jabhi pc frame tayar karega wo uspar source MAC address aur destination MAC address lagakar tayar karega

---

## MAC

- duniya ke har ek ethernet network card ke ROM ke andar 6 Byte ka 48 bit ka hexadecimal address store hota hai aur ye address hamesha unique hota hai 
- ye unique kaise banega to is address ka pehla 3 Byte IEEE control karta hai aur IEE isko OUI ( Organizational Unique Identifier ) yani manufacturer's code kehta hai
- me manufacturer jab IEEE ke pass jaunga to IEEE ke pass jo pehla 3 Byte unique hoga wo mujh jaise munufacturer ko assign kardega 
- ab me manufacturer jitne network card manufacture karunga har network card ke ROM me pehla 3 Byte wahi rakhunga jo IEEE se mila hai aur baad ka 3 Byte apne end se unique bana bana karke lagaunga 
- is prakar se jitne bhi network card me banaunga un har network card ke ROM ke andar ye 6 Byte ka 48 bit ka hexadecimal address jo banega wo hamesha unique banega 
- aur isi ko kuch log BEA ( Burning Address ), physical address, hardware address, machine address, layer 2 address ye sab kuch aur nahi MAC address hai isko alag alag naam se bhi kaha jaata hai.

---

- It may so happen that 2 or more computers may feel like communicating at the same instance.
- If they sense the medium and find that medium is available and put their frames on wire at same instance then these frames on wire will get collided.
- As per CSMA/CD : because it is a democratic world collisions are bound to happen but collisions are not an issue as CSMA/CD has collision detection and avoidance mechanism.

## Collision Detection

- Because there are 2 parts of technology ( Layer 1 & 2 ) hence collision should be evaluated from both layers perspective.

**Collision Detection from Layer 2 perspective** :
- When computers L2 s/w will create frame it will apply SMAC ( Source MAC Address ) and DMAC ( Destination MAC Address ) to the data, at the same time it will also apply CRC code for data integrity check.
- When 2 computers will put their frame on wire at same instance, this frame will get converted to electrical signal, and get collided on wire. 
- Electrical signal is a form of energy that can not be created nor destroyed, but will get distorted on colliding, this collided signal will not vanish but will be resonated back to all computers.
- On receiving this signal L2 S/W will convert it to frame and check integrity and discard it as corrupt frame.

**Collision detection from Layer 1 perspective** : 
- When 2 computers will put their frame on wire at same instance, this frame will get converted electrical signal, and get collided on wire.
- Electrical signal is form of energy that can not be created nor destroyed, but will get distorted on colliding, this collided signal will not vanish off but will be resonated back to all computers.
- Computers that were sending signal will suddenly start realizing that what ever they are sending is getting corrupted and they will immediately back off and the one that detected corruption first will start pumping jamming pattern on wire.
- On receiving jamming pattern all computers will back off and release medium, in this way L1 will react to the collision.

## Collision Avoidance

- On Multi-access medium if there are multiple communicating pairs, wanting to send multiple segment, it will never so happen that on acquiring the medium computers will put all their frames at one shot, for every segment that computer has to send it will have to sense the medium, for next frame it will again have to sense the medium if available acquire it and put the next frame, in this way computer will never push all its segment at one go.
- If there are multiple communicating pairs with multiple segments to be delivered, then to deliver these segments they will keep bidding to acquire medium and keep colliding again and again. So just detecting collision once will not help, there has to be some collision avoidance mechanism.