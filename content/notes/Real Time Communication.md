Link : [[CCNA]]

# Lecture 4

## Real Time Communication

- Real time communication kya hota hai
- mere machine ke hard drive me store mp3 file aur mp4 file real time voice aur video nahi hota hai
- toh real time communication kya hota hai ?
- jo bhi awaj hamare mukh se nikalta hai
- hamare phone ke craddle ke through pass hokar ke tumhare phone ke craddle ke speaker ke through usi waqt jo kano tak pahuche ye real time voice hota hai
- jo bhi image mere camera ne capture kiya usi waqt jo tere screen tak relay hua ye real time video hai
- machine me stored mp3 file mp4 file ise real time voice, video nahi kehte ye sab data hota hai
- jo real time communication hoga isi ke liye real time packet banenge
- toh ya real time packet voice ka banega ya real time packet video ka banega
- aur jo real time service hote hai usko ek parameter control karta hai isko hum quality of experience kehte hai aur quality of experience ko 3 chije monitor karengi 
- pehle delay yani ki latency
- dusra gitter yani inconsistency delay
- teesra drop
- agar real time communication me delay gitter ya drop ayega to user ke experience ki pungi baj jayegi
- iska ye matlab hai real time communication me delay gitter ya drop nahi aana chahiye

---
## Real Time Voice Communication

- Hum humans jo bhi bolte hai usko analogue voice kehte hai
- Machine ko analogue voice samjhta nahi hai
- mera ip phone analogue voice ko digital voice me convert karega yani digitization karega
- phir us digital voice ko packetize karega yani ip address ki marking lagayega
- aur phir usko ip world packet world par realease kar dega
- manle mene phone uthakarke bola 'hello' 
- toh mera ip phone jayega aur 'hello' ke multiple samples banyega
- manle transmit karte karte agar ek aada e ka sample drop hojata hai to usse experience kharab nahi hota 
- but moreover hum humans ki madad se program kiya hua ek software ki madad se artificial intelligence chalta hai in iphone phones par jisko hum kehte hai VCP yani voice concealment program 
- Concealment program dekhega agar koi sample drop hua hai to usko fill karne ke liye ya to previous sample ko replicate karke lagayega ya to latest sample replicate karke lageyaga kuch bhi lagayega mere kano ko drop mehsus hone nahi dega
- voice communication ke andar jo voice ka packet size hoga wo 8 byte se lekar ke 64 bytes tak hoga
- voice ko kya nahi chalta ? Delay
- voice is delay sensitive communication
- to gitter aur drop chalega ? answer hai ghanta
- Real world ho ya ip world ho delay gitter aur drop nahi chalta 
- qunki ye ip world hai to iske kuch advantages hai 
- advantages jaise 1 in 10 thousand voice packet agar kabhi drop hua to concealment program conceal karke kaam chala lega har dusra packet drop nahi hona chahiye
- voice communication me 3 type ke voice sunayi dete hai
- pehla best quality voice for best quality sound delay should be less than 50 millisecond
- for telco quality voice delay should be less than 150 millisecond
- for internet quality voice delay should be less than 200 millisecond

---

## Real Time Video Communication