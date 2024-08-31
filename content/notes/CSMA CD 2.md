Link : [[CCNA]]

# Lecture 9

## How collision is avoided

- After collision computers will enter to their integral wait state, computers calculate their wait state on their own and it has nothing to do with neighbors wait state. 
- These wait states are in microseconds and not in milliseconds they are in multiple of 51.2 microseconds.
- As these wait states are integral computers can increase and reduce their wait states depending on collision, say for example if computer receives more than 5 collisions a second it will understand that there are too many communicating devices wanting to communicate. So as a good citizen it will increase its wait state thereby providing more time to other communicating devices to finish of their communication.
- If lesser collisions are happening the computers can also reduce its wait state. When computers are waiting they can not talk but can listen.
- In our example after collision computers will enter respective wait state, after collision first opportunity will be provided to DDD as its wait state expires in 51.2 microseconds, for next 51.2 microseconds it is lone communicator on the entire medium. 
- Will keep sensing and pushing segments one bye one. After next 51.2 microseconds AAA & CCC will also come out of their wait state and now all 3 computers can communicate on medium with 2, 3, 20 or 50 computers collision will seldom occur, but if it reoccurs then computer will again follow same process and back off, even BBB will back of  and all computers will enter new wait state, if collision does not occur then after 153.6 microseconds democracy returns and all computers can communicate at their will.
- In this way by entering into wait state and providing other computers more time to finish off communication computers try to avoid further collision.

CSMA/CD ke 2 flows hai 
1. jab ek baat karta hai to baki sablogo ko sunna padta hai
2. Jaise 2 log baat kar rahe hai to yaha pe collision ho rha hai

ye problem bus topology me dikhta tha par ab industry me har jagah star topology use hota hai aur star topology me aisa problem nahi dikhta

solution 1 :
- switch allows simultaneous communication between multiple communicating pairs connected on different ports

solution 2 :
- switch 2 prakar ka communication support karta hai half duplex and full duplex 
- half duplex yani jab ek baat karega dusra sunega 
- aur full duplex yani dono sath me bol bhi sakte hai aur sath me sun bhi sakte hai 
- and switches will support half duplex and full duplex communication


Agar koi bole detection aur avoidance dono alag alag padhne ka sath me nahi padhne ka answer hai ghanta

- Wired LAN or Wireless LAN both are 802.3 LAN and work on fundamentals of CSMA/CD and will use some frames MAC, CRC, etc.
- On wired LAN computers are connected using wires and on wireless LAN communication is on air medium.
- In wired LAN communication takes place on confined medium and collisions are immediately detected.
- Communication in air is not confined and collision cannot be immediately detected on some channel. Hence, collision should be avoided as it cannot be detected, So on Wireless LAN we only have CSMA/CA and not CSMA/CD.
- On wireless LAN we use RTS and CTS control signals to avoid collision.
- This proves that collision avoidance is mandatory part of CSMA/CD.


> [!NOTE] 
> Today no one uses bus topology every industry uses star topology


---

## Types of communication

- Communication 3 type ke hote hai.
- Unicast yani ek liye, Multicast yani ek group ke liye, Broadcast yani sabke liye.
- isi prakar se is prithvi ka har communicating device 3 prakar ke frames ya packet ko accept karta hai 
- pehla wo frame ya wo packet jo uske khudke ip ya khudke MAC Address ke liye aya to usko accept karega 
- dusra wo jis group ko belong ko karta hai agar group ke ip ya group ke MAC Address ke liye to bhi usko accept karega 
- aur teesra wo jo sabke ip ya sabke MAC Address ke liye aya to bhi wo usko accept karega.


