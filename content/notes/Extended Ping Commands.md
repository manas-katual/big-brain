Link : [[CCNA]]

# Lecture 10

## Doodh ka doodh paani ka paani

- Jaise mene apne machine par ethernet network card install kar liya to Technology ka Layer 1 install hogaya
- Quki Technology ke 2 part hote hai Layer 1 and Layer 2
- Layer 1 bole to Hardware
- Layer 2 bole to Software, logics, protocols which drives communication over this hardware.
- ab ye Layer 2 software, logics, protocols kya hoga to drivers ye wahi 802.3 ke standard tehet CSMA/CD fundamental par kaam karne wala ARPA protocol wala software, logics, protocol hai jo is hardware par communication ko drive karta hai.
- ek baar hamne succesfully Layer 1 aur Layer 2 install kar liya to agar Microsoft ka PC hai to niche se popup ayega Notification agyega ki ethernet technology is ready for communication LAN card 1 is ready for communication.
- Technology communication karne ke liye tayaar hogaya par kya technology khud communication kar sakta hai ? No
- kisi na kisi ko technology ko use karna padega communication karne ke liye technology khud communication nahi karta.
- Voice communication me user directly interact karta hai technology ke sath communication karne ke liye par data communication me aisa nahi hota me ek end par wire faad ke information daalta nahi hu dusre end pe wire faad ke information nikalta nahi hu mere aur mere is technology ke bich me aisa koi agent chahiye hoga aisa koi mediation Layer chahiye hoga jo ek end par user se information lega niche technology ko dega dusre end par technology se information lega aur user ko dega aise mediation Layer ko aise agent ko hum "upper Layer Protocol Stack" kehte hai. 
- Aur "Upper Layer Protocol stack" 3 type ke hote hai
- IP, IPX and AT ( Apple Talk ) but IPX and AT obsolete ho chuka hai inko koi use nahi karta hai to abse jo bhi communication hota IP ka hi hota hai 
- IP kya hai ? IP is collection of multiple tools and software.
- jaise file bhejna hai to FTP, remote access lena hai to Telnet 
- Toh telnet, FTP, HTTP aise aneko tool ka collection hai IP koi single tool ya software nahi hai 

==diagram==

**IP communication kaam kaise karega**
Example :
- jab me is PC par baith karke likhunga `ftp 10.0.0.4` to IP ka ftp tool activate ho jayega 
- phir mene likha `put Ash.jpg` to put ye command ko pehle se hi pata hoga ki mere machine ke hard drive me kaha par ye 700 Aishwarya stored hai
- sidhe uthakar daalega ? No.
- koi ek software is 700 mb file ke chote chote segment karega, koi ek software in segment ko mark karega, koi ek software ispar CRC code lagayega, koi ek software niche ke technology ko laat marke bolega leja aur deliver karke aa, dusre end par koi ek software isko niche ke technology se receive karega, koi ek software CRC code check karega satheek hai perfect hai toh usko accept karega phir acknowledgement bhejega for next segment.
- is prakar se jab saare tukde aajayenge to jaise waha toda tha waise yaha jodega aur user ko present karega 
- iska ye matlab hai ki technology ko jyada se jyada Layer 1 and Layer 2 hi samjhta hai yani wo ek packet ka CRC code hi check karke ya to accept kar sakta hai ya to retransmit kar sakta hai.
- lekin end to end error free successful communication ki guarantee technology nahi dega ye "IP Upper Layer Protocol stack" deta hai
- aur IP end to end error free successful communication ki guarantee acknowledgment aur retransmission ki madad se deta hai 
- ab yaha par punch statement kya bana toh communication ip ka ho raha hai user ke behalf par ho raha hai underline technology ko use karke ye communication ho raha hai
---

**Reverse Gear**

- toh jaise mene apne machine me ethernet network card successfully install kardiya  to ab us network card ye kaise pata chalega ki us jo communication karna hai wo saara ka saara IP ka karna hai
- to ye administrator jab network card ke properties me jayega TCP IPv4 ko select karega to hamne hi ye jaakar bind kardiya ki is network card par abse jo bhi communication hoga wo saara ka saara IP ka hoga 
- are ip ka communication hoga toh ip address dena padega to kya hum Ip address PC ko de ? nahi. Ip address PC ko nahi diya jaata ip address PC ke ethernet network card ko diya jaata hai agar machine me aise 10 network card bhi honge toh 10 par hum alag alag ip assign karenge 
- ab network card par jo hum ip de rahe hai iska information store kaha hoga
- toh duniya ke har ek Operating System ke andar /etc directory hogi jisme aneko ip associated tables honge jinme se ek table hoga ARP table
- ARP table ye wo table hota hai jaha saare ip address aur uske MAC address ka mapping stored hota hai 
- lekin har ARP table me initially kewal khudka ip aur khudka MAC hoga gradually wo baki sab ip aur MAC ko learn karega
- waise hi ek aur host table hota hai jo batata hai ki tera PC ek host hai aur uska kya ip address hai 
- Similarly ek aur table hoga routing table jo batayega tere device me kitne network card hai aur unka ip address kya hai 
- yehi wo table hai jinko kaha jaata hai ip associated table aur yahi wo table hai jo hamare network card par diye hue ip ke information ko store karenge yani retain karenge.


==diagram==

**Final flow**

- jaise is pc par baitha hua banda bolega `ftp 10.0.0.4` yani ip ka FTP tool activate hogaya 
- phir likha `put Ash.jpg` to put ye command ko pehle se hi pata hoga ki mere machine ke hard drive me kaha par ye 700 mb Aishwarya stored hai
- sidhe uthakar daalega ? No.
- koi ek software is 700 mb file ke chote chote segment karega, koi ek software in segment ko mark karega, koi ek software ispar CRC code lagayega, koi ek software niche ke technology ko laat marke bolega leja aur 10.0.0.4 ko deliver karke aa, 
- toh technology bolega ghanta nahi jaunga q quki me technology hu agar mujhe kuch samjhta hai to wo Layer 2 ka address samjhta hai which is MAC Address me ip wagere kuch samjhta nahi hu agar tujhe ip ka MAC address chahiye to tera PC apne ARP table pe jayega q quki ARP table ye wo table hota hai jaha saare ip address aur uske MAC address ka mapping stored hota hai lekin mere ARP table me shuruat me kewal mera ip aur mera MAC hoga me pehle se 10.0.0.4 ka MAC jaanta nahi hu agar nahi jaanta to ab tere PC ka ARP wala jo software hai wo ab activate hoga aur ARP broadcast karega.
- What is ARP Broadcast ? Send IP request for MAC address. Broadcast me likhega jo koi bhi 10.0.0.4 hai apna MAC address de na yaar ab jo 10.0.0.4 hoga wo broadcast accept karega baki sab isko discard karenge ek baar reply aya to mera PC pehle apne ARP Table pe jayega aur likh dega ki 10.0.0.4 ka MAC address hai DDD ab technology ko laat marke bolega leja saale aur DDD isko deliver karke aa technology kya uska baap bhi jayega

---

## Ping

- Ping is a tool or application of IP Upper Layer Protocol stack, that is used to get network layer/IP layer/Layer 3 status.
- Ping sends ICMP echo packets to get network layer status.
- Ping is also used for following
	- To check connectivity
	- to calculate Latency ( Delay )
	- To verify Link quality (Drops)
- Results of ping may not be relevant for real time packets used over QOS enabled path.
- For QOS enabled path we can used IP packets with different sizes and TOS marking (184 for voice pkt & 136 for video pkt)