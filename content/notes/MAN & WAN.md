Link : [[CCNA]]

# Lecture 5

==Diagram==

**Question :**

5 mb bandwidth hai aur 3 services ek sath aage jaane ke liye aaya hai 64 kb ka voice aya 700 mb ka data aya hai aur 8 mb ka live video feed aya hai in 3no me sabse pehle aage kon jayega ?

**Answer :**

- Me pehli dhaar ka tha sabse pehle hamne kaha data jayega 
- toh yaha par pehle data nahi jaa sakta
- quki agar 5 mb pura data occupy kar lega toh usi waqt aye hue voice aur video ko rukna padega aur agar voice ko roka to voice me delay aajyega aur voice ko delay nahi chalta 
- toh yaha par hamesha sabse pehle voice jayega phir video jayega aur last me data jayega 
- ab yaha par pehle video bhi nahi jaa sakta quki problem bandwidth ka hai 
- bandwidth hai 5 mb aur video ka size hai 8 mb 
- toh 8 mb ka jab video ayega 5 mb par 8 mb me se 5 mb chala jayega 3 mb buffer ( switch device me temporary storage hota hai 16 mb ) ke andar store ho jayega dubara 8 mb ka video packet khada hai toh buffer me total 11 mb store hai jaise hi 5 mb bandwidth khali hoga 11 me 5 mb chala gaya to 6 mb bach gaya dubara 8 mb ka video piche khada hai to total 14 mb hogaya ab 14 me se jaise bandwidth khali hoga 5 mb chala jayega 9 mb bach jayega dubara 8 mb piche khada hai total 17 mb ho jayega par buffer me unlimited storage nahi hota manle switch me 16 mb ka capacity hai to 15 mb tak ka toh wo store kar lega jaisa content 16 mb se jyada badhega to naye content ko store karne ke liye existing content ko drop karna pad sakta hai ya existing content ko retain karne ke liye naye content ko drop karna pad sakta hai kisi bhi content ko drop kiya to video me drop ajayega par video ko drop nahi chalta 
- toh yaha par problem bandwidth ka hai minimum itna bandwidth to lena hi padega jitna real time services ko chahiye
- jaise yaha par voice ko 64 kb aur video ko 8 mb yani total 9 mb ki requirement hai
- agar hamne bandwidth 10 mb liya hota toh yaha par voice aur video 9 mb me nikal jata
- 1 mb par agar me data bhejta tabhi sab perfect chalta quki data ko kuch farak nahi padta ki data kab pahuchega kitne retransmission ke baad pahuchega ya kitne drop ke baad pahuchega ek hi chij hota ki data jabhi pahuchega sathik pahuchega ekdam perfect pahuchega


**but 2 problems :**

problem 1 : 
Device ko kaise samajh me ayega ki in 3 services me se konsa service voice ka hai konsa video ka hai aur konsa data ka hai

Answer :
ip address me takat hota hai ki ye jabhi koi service tayaar karega wo har service ko mark karega ki ye service voice ka hai ye service video ka hai aur ye service data ka hai 

problem 2 :
device ko ye kaisa samajta hai ki voice ka quality requirement kehta hai ki voice ko delay nahi chaega video ka quality requirement kehta hai video ko drop nahi chalega aur data ka quality requirement kehta hai ki data ko sab chalega ?

Answer :
Quality of Service yani classification and prioritization ye classify karta hai konsa service voice ka konsa video ka hai aur konsa data ka hai aur prioritize karta hai voice over video over data 

---

**Characteristic no. 6 :**

LANs administrative control should be centralized

meaning : 
we don't need 6 employees for a single job 

---

## MAN ( Metropolitan area network )

Definition :
Two or more computers or communicating devices or networks which are geographically seperated but within same metro city if connected are said be connected on MAN


---

## WAN ( Wide area network )

Definition :
Two or more computers or communicating devices or networks which are geographically seperated but not within same metro city if connected are said be connected on WAN

---

==Diagram==

Characteristic no. 1 :

Man or WAN should be capable of providing high to moderate bandwidth connectivity where limiting factor is cost

- HDFC ke do branch office hai ek mulund me aur ek thane me
- HDFC ko agar apne do branch ko sathme connect karna hai to wo zameen khod ke khudka wire nahi daalenge
- market me aneko service provider hai
- wo service provider se apne do branch ke liye ek "Dedicated Leased Line" lega
- iske liye service provider bohot premium charge karega
- jab bhi itna link yani circuit liya jayega toh yaha par hum konsi services chalayenge aur un services ke liye konsi bandwidth chahiye iske liye bandwidth ka services ka capacity ka planning karna padega 
- For example mulund aur thane ko milakar thousand employee kaam karte hai 
- to because HDFC is bank
- bank ko voice ki itni jarurat nahi hai lekin 1000 ka 10% 100 log agar 64 kb ka voice use kiye to voice ke liye lagbhag lag jayega 6.4 mb
- Similarly, voice ke sath video ki bhi HDFC ko requirement nahi hai lekin phir bhi video conferencing ke liye 100 me 10% 10 log agar video 640 kb ka bhi kiye to video ke liye bhi lagbhag lag jayega 6.4 mb
- Similarly, data ka at present requirement 1 mb hai but future ko mind me rakhte hue 10 mb extra demand kar liya aur nayi requirement 10 mb ki data ki ban gayi
- toh voice, video aur data ko milakar HDFC ko approximately 23 mb required hai
- market me alag alag type ki service hai 
- jaise 
	- T1 circuit
	- E1 circuit
	- E3 circuit
	- T3 circuit
	- STM1/OC3
	- STM64/OC192
- isme se koi bhi lag sakta hai lekin agar bohot paisa hai to 10 gb ka laga le koi gam nahi
- lekin paisa jyada nahi hai to utna hi bandwidth lena chahiye jitna humko requirement hai