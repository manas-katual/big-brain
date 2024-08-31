Link : [[CCNA]]

# Lecture 11

## Proof ping

- kaise proof kiya jayega ping ye command connectivity test ke liye banaya nahi hai 
- to puchneka kya tune kabhi universal loop back address ke baare me suna hai kya tune kabhi local host address ke baare me suna hai 
- 127.0.0.0 - 127.255.255.255 ye pura range universal loop back address ka range hai aur is range ka jo sabse pehla wala ip address hai which is 127.0.0.1 ye local host address hota hai
- ye pura range aur ye address software developers ke liye banaya gaya hai
- agar me koi aisa software bana raha hu jiska ek copy printer par dena chahta hu aur duplicate copy locally machine par store karna chahata hu to machine ka address mujhe pehle se kaise pata chalega 
- isliye har pc ko pehle se hi ek khudka address de diya gaya hai jisko hum local host address kehte hai aur wo address hai 127.0.0.1
- toh ab me apne software me likh dunga ki duplicate copy 127.0.0.1 pe store karna hai toh ab ye software prithvi ke jis bhi device pe chalega wo har device ke liye 127.0.0.1 wo khud hoga toh hamesha locally store karega aur kahi par bhi store karne wala nahi hai 
- ab agar ye tu janta hai toh tu ja apne machine ke saare wire cable, connector, network adapter sabko disable kar daal ab command prompt par jaake ping kar 127.0.0.1 ko ye 100% ping hoga agar ye ping hua toh ye itna to proof kar hi dega ping ye command connectivity to test karne ke liye banaya nahi hai wo kar sakta hai wo byproduct hai lekin wo uska primary purpose nahi hai 
- primary purpose ek hi hai wo hai IP Layer, Network Layer, Layer 3 status information lana
- 127.0.0.0 - 127.255.255.255 ye pura range machine ke andar communication karne ke liye reserve kiya gaya hai. ye lekar ke me machine ke bahar dusre machine se communicate nahi kar sakta 
- ab machine ke andar kaisa communication hoga for example mere machine me ek application ko agar time ka information chahiye to usko NTP (Network Time Protocol) ke pass jaana hoga yahi wo s/w hai jo time ke information ko manage aur mantain karta hai lekin NTP kidhar milega toh NTP ko bhi ek address pehle se deke rakha gaya hai which is 127.127.7.1 to wo application is address par jayega NTP se time ka information la karke display karna start karega toh aise machine ke andar communication karne ke liye is range banaya gaya hai ye le karke me machine ke bahar dusre machine se communicate nahi kar sakta

---
## IP Flow

==diagram==

- Jaise is PC par baitha hua banda bolega ping 10.0.0.4 yani ki usko 10.0.0.4 ka network Layer status chahiye
- ab ye pc ek frame tayaar karega jisme sabse pehla field hoga Data ka jaha likha hoga mujhko tera network Layer status chahiye jab ye data jayega tabhi to status ayega agar data bhejna hai to uske aage aneko headers lagane padenge headers me sabse pehla field hoga Source IP. Source IP boleto khudka IP. IP boleto Layer 3 information
- ab mera PC apne L3 routing table ke pass jayega aur puchega apna ip address kya hai ye bolega hamare pass ek hi network card hai jiska IP address hai 10.0.0.1. uthakar likh dega 10.0.0.1 
- next field hai destination IP. DIP boleto jaha jaana hai uska IP. IP bole to L3 information command se uthakar likhne se pehle kahani me twist hai
- ab mera PC apne L3 routing table ke pass jayega aur puchega kya hum 10.0.0.0 network ko pohoch sakte hai ye bolega ha hamare pass ek hi network card jo usi network ko belong karta hai to hum pohoch sakte hai uthakar likh dega 10.0.0.4
- next field hai source MAC, Source IP ka MAC, MAC bolete L2 information ab mera PC apne L2 ARP table ke pass jayega aur puchega 10.0.0.1 ka MAC address kya hai ye bolega AAA uthakar likh dega AAA 
- next field hai destination MAC, destination MAC bole to jaha jaana hai uska MAC, MAC bole to L2 information ab mera PC apne L2 ARP table ke pass jayega aur puchega 10.0.0.4 ka MAC address kya hai ye bolega malum nahi to yehi par ek punch statement hai agar L2 par destination MAC address malum nahi hai toh mera PC ab ARP broadcast bhejega ARP broadcast yani send IP address for MAC address to ab is frame ko uthakar side me park kar dega aur ek naya broadcast frame tayaar karega jisme sabse pehla field hoga data ka jaha likha hoga jo koi bhi 10.0.0.4 hai apna MAC address dena yaar source IP ab wo IP hoga jisko MAC address chahiye destination IP uska IP hoga jiska MAC address chahiye Source MAC bole to source IP ka MAC uthakar likh dega AAA quki L2 par broadcast bheja jaa rha hai to L2 ka broadcast address hota hai ff:ff:ff:ff:ff:ff 6 baar waise hi L3 ka broadcast address hota hai 255.255.255.255
- toh L2 ka broadcast address yaha par laga diya jayega which is ff:ff:ff:ff:ff:ff ab jaise ye broadcast frame wire pe jayega electrical signal me convert ho jayega sabhi ko eksath milega lekin accept kewal wahi karega jiske liye broadcast aya hai baki sab isko discard kar denge.
- Jaise DDD accept karke reply bheja toh ab mera PC jayega pehle apne ARP table me ab entry bana dega ki 10.0.0.4 ka MAC address hai DDD ab parked frame ko dubara picture laya jayega aur likh diya jayega MAC address hai DDD is prakar se broadcast bhej karke MAC learn kiya jaata hai


---

## Full fledged IP flow

- Jaise ye broadcast frame wire par jayega electrical signal me convert ho jayega sabhi ko ek sath hi milega lekin samajhne ke liye ek ek karke samjhenge
- Jaise ye broadcast frame BBB ke pass ayega BBB ke L1 se L2 par ayega BBB ka L2 s/w L2 information kholega aur puchega kaha jaana hai ye bolega fff ye bolega lekin me to BBB hu tu mere liye nahi aya hai quki tu broadcast hai yani tu sabke liye aya isliye me bhi tujhe accept karta hu
- BBB ka L2 s/w L2 information uthakar side me rakh dega bacha hua information upar ke L3 ko de dega 
- L3 s/w ab L3 information kholega aur puchega kaha jaana hai ye bolega 10.0.0.4 ye bolega lekin me to 10.0.0.2 hu tu mere liye nahi aya hai isliye me tujhe discard karta hu
- Lekin discard karne se pehle yaha par ek ghanghor baapta hai yaha par is PC ne is frame ka L2 information bhi khola aur L3 information bhi khola isko L2 ke baare me bhi pata chala aur L3 ke baare me bhi pata chala to ye jayega apne ARP table me ye likh dega 10.0.0.1 ka MAC Address hai AAA ab is frame ko discard kar dega 



- Similarly, Jaise ye broadcast frame wire par jayega electrical signal me convert ho jayega sabhi ko ek sath hi milega lekin samajhne ke liye ek ek karke samjhenge
- Jaise ye broadcast frame CCC ke pass ayega CCC ke L1 se L2 par ayega CCC ka L2 s/w L2 information kholega aur puchega kaha jaana hai ye bolega fff ye bolega lekin me to CCC hu tu mere liye nahi aya hai quki tu broadcast hai yani tu sabke liye aya isliye me bhi tujhe accept karta hu
- CCC ka L2 s/w L2 information uthakar side me rakh dega bacha hua information upar ke L3 ko de dega 
- L3 s/w ab L3 information kholega aur puchega kaha jaana hai ye bolega 10.0.0.4 ye bolega lekin me to 10.0.0.3 hu tu mere liye nahi aya hai isliye me tujhe discard karta hu
- Lekin discard karne se pehle yaha par yaha par bhi ek ghanghor baapta hai yaha par is PC ne is frame ka L2 information bhi khola aur L3 information bhi khola isko L2 ke baare me bhi pata chala aur L3 ke baare me bhi pata chala to ye bhi jayega apne ARP table me ye likh dega 10.0.0.1 ka MAC Address hai AAA ab is frame ko discard kar dega 


- Similarly, Jaise ye broadcast frame wire par jayega electrical signal me convert ho jayega sabhi ko ek sath hi milega lekin samajhne ke liye ek ek karke samjhenge
- Jaise ye broadcast frame DDD ke pass ayega DDD ke L1 se L2 par ayega DDD ka L2 s/w L2 information kholega aur puchega kaha jaana hai ye bolega fff ye bolega lekin me to DDD hu tu mere liye nahi aya hai quki tu broadcast hai yani tu sabke liye aya isliye me bhi tujhe accept karta hu
- DDD ka L2 s/w L2 information uthakar side me rakh dega bacha hua information upar ke L3 ko de dega 
- L3 s/w ab L3 information kholega aur puchega kaha jaana hai ye bolega 10.0.0.4 ye bolega are me hi hu 10.0.0.4 tu saale mere liye hi aya hai 
- L3 s/w ab L3 information uthakar side me rakh dega lekin bacha hua data upar ke s/w ko dene se pehle
- yaha par bhi ek ghanghor baapta hai yaha par is PC ne is frame ka L2 information bhi khola aur L3 information bhi khola isko L2 ke baare me bhi pata chala aur L3 ke baare me bhi pata chala to ye jayega apne ARP table me ye likh dega 10.0.0.1 ka MAC Address hai AAA ab upar ka s/w data kholega aur padhega ki mera MAC address maang raha hai 
- to ab reply frame tayaar karega jisme sabse pehla field hoga data jaha likha hoga mera MAC address hai DDD jo request me source IP tha reply me wo Destination IP ban jayega request ka destination IP jo tha reply me wo source IP ban jayega source MAC bole to source IP ka MAC khudka MAC likh dega DDD aur destination MAC bole to wo MAC jaha is frame ko jana hai isko kaha jaana hai ? 10.0.0.1
- to ye apne ARP table ke pass jayega aur puchega 10.0.0.1 ka MAC address kya hai agar malum hai to wahi se uthakar likh dega AAA 


- ab jaise ye reply frame wire par jayega electrical signal me convert ho jayega sabhi ko ek sath hi milega lekin samajhne ke liye ek ek karke samjhenge
- Jaise ye broadcast frame CCC ke pass jayega CCC ke L1 se L2 par jayega CCC ka L2 s/w L2 information kholega aur puchega kaha jaana hai ye bolega AAA ye bolega lekin me to CCC hu tu mere liye nahi aya hai isliye me tujhe discard karta hu 
- dhyan se dekh yaha L2 kholke hi pata kar liya ki frame uske aya nahi hai to kya L3 information khulega ? No toh yaha kuch free ka mapping milne wala nahi hai


- Similarly jaise ye reply frame wire par jayega electrical signal me convert ho jayega sabhi ko ek sath hi milega lekin samajhne ke liye ek ek karke samjhenge
- Jaise ye broadcast frame BBB ke pass jayega BBB ke L1 se L2 par jayega BBB ka L2 s/w L2 information kholega aur puchega kaha jaana hai ye bolega AAA ye bolega lekin me to BBB hu tu mere liye nahi aya hai isliye me tujhe discard karta hu 
- dhyan se dekh yaha L2 kholke hi pata kar liya ki frame uske aya nahi hai to kya L3 information khulega ? No toh yaha kuch free ka mapping milne wala nahi hai


- Similarly, jaise ye reply frame wire par jayega electrical signal me convert ho jayega sabhi ko ek sath hi milega lekin samajhne ke liye ek ek karke samjhenge
- Jaise ye broadcast frame AAA ke pass ayega AAA ke L1 se L2 par ayega AAA ka L2 s/w L2 information kholega aur puchega kaha jaana hai ye bolega AAA ye bolega me hi hu AAA tu saale mere liye hi aya hai 
- L2 s/w ab L2 information uthakar side me rakh dega bacha hua information upar ke L3 ko dega L3 s/w L3 information kholega aur puchega kaha jaana hai ye bolega 10.0.0.1 ye bolega are me hi hu 10.0.0.1 tu saale mere liye hi aya hai 
- L3 s/w L3 information uthakar side me rakh dega bacha hua data upar ke s/w ko dene se pehle yaha par ek ghanghor baapta hai yaha par is PC ne is frame ka L2 information bhi khola aur L3 information bhi khola isko L2 ke baare me bhi pata chala aur L3 ke baare me bhi pata chala to ye  jayega apne ARP table me ye ghis dega 10.0.0.4 ka MAC Address hai DDD ab upar ka s/w jo broadcast bheja tha jab reply ayega toh dekhega MAC address mila hai DDD wo ARP table ke pass jayega lekin dekhega yaar entry to pehle se hi hai toh usko overwrite kar dega aur phir parked frame ko dubara picture me laya jayega aur likh diya jayega destination MAC address hai DDD
- aur is prakar se broadcast jaata hai aur uska reply aata hai 
