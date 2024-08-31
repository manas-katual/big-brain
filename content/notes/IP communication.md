Link : [[CCNA]]

# Lecture 3

## IP Communication

IP Communication is a communication in which every device gets a unique ip address and communication between them happens in the form of packets. and ip has capability of classifying services by marking at source ( it can mark which is voice packet and video packet )


## How IP communication works

- Jab ip phones ip address lekar up ( start ) honge.
- pehla step ye jayenge aur khudko PBX ke sath register karenge.
- Register karne ke liye ye control packet bhejenge.
- Jisme bolega a bhai mera ip address 10.0.0.1 hai mujhko ek extension number de
- PBX ye wahi device hai jiske pass saare ip address aur uske extension number ka mapping stored hota hai 
- ye reply me bateyga tera extension number hai 101
- Similarly, jab ye ip phone ip address lekar ke up ( start ) hoga.
- pehla step ye bhi jayega aur khudko PBX ke sath register karega.
- Register karne ke liye control packet bhejega 
- Jisme bolega a bhai mera ip address 10.0.0.2 hai mujhko bhi ek extension number de
- PBX ye wahi device hai jiske pass saare ip address aur uske extension number ka mapping stored hota hai
- toh ye reply me bateyga tera extension number hai 102
- ek baar jab hum register hue to jab ek human dusre human ka number dial karega.
- toh kya wo immediately prakat hojayega aur baat karne lagega ? answer is no.
- ek human dusre human ko uske naam se uske phone number se uske email address se pehchanta hai
- Lekin mera ip phone tere ip phone ko tere ip address se pehchanega.
- Lekin kya mujhe tera ip address pehle se pata hoga ? answer is no.
- Me nahi jaanta to tera ip address ek aur device hai jo jaanta hai wo kon hai ? answer is PBX.
- toh jab hum dial karenge 102 
- toh mera ip phone dubara PBX ka pass jayega aur puchega 102 extension number ka ip address kya hai ye bolega 10.0.0.2
- jab extension number dega usi waqt yaha ( 10.0.0.2 ) ring bajayega "shaka laka boom boom boom boom" aur yaha ( 10.0.0.1 ) par dial tone "trrr trrr trrr trrrr"
- jaise ye banda ab phone uthayega me human jo bhi yaha bolunga wo saara analogue voice ko mera ip iphone digital voice me convert karega phir digital voice ko packetize karega packetize karne ka matlab uspar ip address ka marking lagayega
- jaha source ip address mere ip address ka lagega aur destination ip address samne wale ke ip address ka lagega 
- aur ye packet direct yaha se waha forward kar diya jayega
- kya ye packet ek bhi baar via PBX hokar gaya ? NO.
- toh PBX INLINE device nahi raha ye ON NET device ban gaya hai
- Agar communication iske via nahi hoga to mehenga device yaha lagane ka jarurat nahi hai 

---
## How video communication works over IP 

- me agar pradeep@hotmail se baat karna chahta hu 
- toh me aur pradeep dono sabse pehle jayenge MS Teams ke MCU par register karenge
- jab hum register kar dalenge teams ka MCU jan jayega ki hamara email address kya hai aur hamara ip address kya hai
- ab jab ek human dusre human ko connect karne ke liye uska email address likhega aur double click karega to kya human immediately prakat hojayeg aur baat karne lagega ? NO
- are me human hu me toh dusre ko uske naam se uske phone number se uske email address pehchanta hu 
- lekin mera pc tere pc ko uske ip address se pehchanta hai
- Lekin mujhe tera address pehle se pata hoga ? NO
- Me nahi jaanta to tera ip address ek aur device hai jo jaanta hai wo kon hai ? answer is MCU.
- toh pehla mera pc MCU ko control packet bhejega aur puchega pradeep@hotmail ka ip address kya hai
- jab ye reply me batayega usi waqt ye ring bajayega "shaka laka boom boom boom boom" aur yaha pe dial tone par "trrr trrr trrr trrr" 
- jaise isne ab mera call accept kiya jo bhi image mera camera capture karega uske ab ye real time packet me convert karega packet me convert karneka matlab uspar ip address ka marking lagayega 
- jaha source ip address mere pc ka lagega aur destination ip address pradeep ke pc ka lagega
- aur ye bhi direct yaha se waha forward kar diya jayega 
- kya ye via MCU gaya ? NO.
- toh MCU bhi communication ke bich me nahi aya to ye inline device nahi raha yani MCU bhi abhi ON NET device ban gaya hai


---
## Real world vs IP world

- Real world ye wo world hota hai jaha saari services ek alag alag frequency par kaam karti hai
	- Example of real world is 
		- **FDM ( Frequency Division Multiplexer ) :** purane jamane me ek hi cable ke wire par multiple channels ek sath aate hai  lekin har ek channel alag alag frequency par aata hai
		- **TDM ( Time Division Multiplexer ) :** ek wire par 32 log ek sec me ek sath baat kiye lekin har banda ek sec me alag alag time slot me baat kar raha hai
- Aur ip world ye world hota hai jaha saari services ek single yani same hi frequency par kaam karti hai
	- Example agar me aur samne wala banda directly connected hai aur agar me ek sec me 1 crore bit bhejta hu to usse bhi ek sec me 1 crore bit sunna padega tu kam ya jyada sunega to tere aur mere bich me communication nahi hoga
	- ab ip world me ye user ke pass privilege hai ki agar wo ek sec me 1 crore bit bhej raha hai to usme kitna bit wo voice ka bheje kitna bit video ka bheje aur kitna bit data ke bheje