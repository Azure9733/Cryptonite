## Challenge
Hi! It's good to see you again in my networking series. There are total 18 challenges in this series & based on real life events of how can a server be compromised. Please download the attachment which will be used to answer all the questions. Don't make it too complex. Just keep it simple. Hope you'll solve them all. Wish you all a very good luck.  
Scenario: Recently one of Knight Squad's asset was compromised. We've figured out most but need your help to investigate the case deeply. As a SOC analyst, analyze the pacp file & identify the issues.  
So let's start with the basic.  
What is the victim & attacker ip?  
Flag Format: KCTF{victimIp_attackerIp}  

## Approach
I downloaded the packet capture and opened it on wireshark. Filter the ARP packets.  
I noticed that the number of packet captures were more than anything I had ever seen and it made sense because until now I was just learning from small captures.  
Most of the captures were TCP Protocol and HTTP. Manually going through the captures was incredibly time consuming so i learnt of a new way. Exporting Objects.  
Going to File-> Export Objects -> HTTP -> Application zip files, i see a suspicious zip file named ``maybeconfidential.zip``.  
From there I was able to jump to that particular packet caputre and see the attacker and victim IP Address.  
![Screenshot 2024-01-21 102756](https://github.com/Azure9733/Cryptonite/assets/143328010/b91cbbc8-f297-4469-a2de-eb06c57dd84c)  
![Screenshot 2024-01-21 111019](https://github.com/Azure9733/Cryptonite/assets/143328010/91ccb047-42f4-41b9-8458-419641403967)  
Flag: ``KCTF{192.168.1.8_192.168.1.7}``
