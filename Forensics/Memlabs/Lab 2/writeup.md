## Description
One of the clients of our company, lost the access to his system due to an unknown error. He is supposedly a very popular "environmental" activist. As a part of the investigation, he told us that his go to applications are browsers, his password managers etc. We hope that you can dig into this memory dump and find his important stuff and give it back to us.
## Clues
1. unknown error
2. browser and password manager
3. environmentalist
## Solution
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/80e2b258-9bef-4cd5-85f7-a79c9edfe5d3)
```
root@a0a6c5d849e3:/mnt/documents/memlabs/lab2# volatility -f MemoryDump_Lab2.raw --profile=Win7SP1x64 pslist
Volatility Foundation Volatility Framework 2.6
Offset(V)          Name                    PID   PPID   Thds     Hnds   Sess  Wow64 Start                          Exit                          
------------------ -------------------- ------ ------ ------ -------- ------ ------ ------------------------------ ------------------------------
0xfffffa8000ca0040 System                    4      0     80      541 ------      0 2019-12-14 10:35:21 UTC+0000                                 
0xfffffa80014976c0 smss.exe                248      4      3       37 ------      0 2019-12-14 10:35:21 UTC+0000                                 
0xfffffa80014fdb30 csrss.exe               320    312     10      446      0      0 2019-12-14 10:35:27 UTC+0000                                 
0xfffffa8001c40060 csrss.exe               368    360      8      237      1      0 2019-12-14 10:35:28 UTC+0000                                 
0xfffffa8000ca8840 psxss.exe               376    248     18      786      0      0 2019-12-14 10:35:28 UTC+0000                                 
0xfffffa8001c5a700 winlogon.exe            416    360      6      112      1      0 2019-12-14 10:35:30 UTC+0000                                 
0xfffffa8001c5b2b0 wininit.exe             424    312      3       75      0      0 2019-12-14 10:35:30 UTC+0000                                 
0xfffffa8001c95320 services.exe            484    424      8      206      0      0 2019-12-14 10:35:31 UTC+0000                                 
0xfffffa8001c9d910 lsass.exe               492    424      8      546      0      0 2019-12-14 10:35:31 UTC+0000                                 
0xfffffa8001c9e2d0 lsm.exe                 500    424     10      181      0      0 2019-12-14 10:35:31 UTC+0000                                 
0xfffffa8001cec790 svchost.exe             588    484     12      354      0      0 2019-12-14 10:35:35 UTC+0000                                 
0xfffffa8001d13060 VBoxService.ex          652    484     14      135      0      0 2019-12-14 10:35:36 UTC+0000                                 
0xfffffa8001d4ab30 svchost.exe             720    484      7      275      0      0 2019-12-14 10:35:37 UTC+0000                                 
0xfffffa8001d76320 svchost.exe             812    484     21      474      0      0 2019-12-14 10:35:38 UTC+0000                                 
0xfffffa8001da6930 svchost.exe             852    484     20      417      0      0 2019-12-14 10:35:38 UTC+0000                                 
0xfffffa8001dacb30 svchost.exe             876    484     39      962      0      0 2019-12-14 10:35:38 UTC+0000                                 
0xfffffa8001df65f0 audiodg.exe             268    812      7      131      0      0 2019-12-14 10:35:41 UTC+0000                                 
0xfffffa8001e1eb30 svchost.exe             472    484     12      301      0      0 2019-12-14 10:35:42 UTC+0000                                 
0xfffffa8001e47740 svchost.exe            1044    484     16      361      0      0 2019-12-14 10:35:43 UTC+0000                                 
0xfffffa8000cf9220 spoolsv.exe            1208    484     13      279      0      0 2019-12-14 10:35:47 UTC+0000                                 
0xfffffa8001ed8b30 svchost.exe            1248    484     18      303      0      0 2019-12-14 10:35:49 UTC+0000                                 
0xfffffa8001f4eb30 svchost.exe            1368    484     23      314      0      0 2019-12-14 10:35:51 UTC+0000                                 
0xfffffa8001f7c060 TCPSVCS.EXE            1412    484      4       97      0      0 2019-12-14 10:35:53 UTC+0000                                 
0xfffffa80020f2b30 taskhost.exe           1928    484      9      154      1      0 2019-12-14 10:36:04 UTC+0000                                 
0xfffffa8002105b30 taskeng.exe            1996    876      5       79      0      0 2019-12-14 10:36:04 UTC+0000                                 
0xfffffa800211e7c0 dwm.exe                2012    852      4       72      1      0 2019-12-14 10:36:04 UTC+0000                                 
0xfffffa8002131340 explorer.exe           1064   2004     37      989      1      0 2019-12-14 10:36:05 UTC+0000                                 
0xfffffa80021bb240 SearchIndexer.         1836    484     12      628      0      0 2019-12-14 10:36:11 UTC+0000                                 
0xfffffa80021c0b30 VBoxTray.exe           1896   1064     13      138      1      0 2019-12-14 10:36:13 UTC+0000                                 
0xfffffa80022a3b30 csrss.exe              2308   2300      9      246      2      0 2019-12-14 10:36:24 UTC+0000                                 
0xfffffa80022a73e0 winlogon.exe           2336   2300      4      109      2      0 2019-12-14 10:36:24 UTC+0000                                 
0xfffffa8000e76060 taskhost.exe           2604    484      9      154      2      0 2019-12-14 10:36:29 UTC+0000                                 
0xfffffa8000e95060 dwm.exe                2652    852      3       71      2      0 2019-12-14 10:36:29 UTC+0000                                 
0xfffffa8000e9a110 explorer.exe           2664   2632     19      632      2      0 2019-12-14 10:36:29 UTC+0000                                 
0xfffffa8000edcb30 VBoxTray.exe           2792   2664     12      139      2      0 2019-12-14 10:36:30 UTC+0000                                 
0xfffffa80022e5950 cmd.exe                2096   2664      1       19      2      0 2019-12-14 10:36:35 UTC+0000                                 
0xfffffa8000e63060 conhost.exe            2068   2308      2       50      2      0 2019-12-14 10:36:35 UTC+0000                                 
0xfffffa8002109b30 chrome.exe             2296   2664     27      658      2      0 2019-12-14 10:36:45 UTC+0000                                 
0xfffffa8001cc7a90 chrome.exe             2304   2296      8       71      2      0 2019-12-14 10:36:45 UTC+0000                                 
0xfffffa8000eea7a0 chrome.exe             2476   2296      2       55      2      0 2019-12-14 10:36:46 UTC+0000                                 
0xfffffa8000ea2b30 chrome.exe             2964   2296     13      295      2      0 2019-12-14 10:36:47 UTC+0000                                 
0xfffffa8000fae6a0 chrome.exe             2572   2296      8      177      2      0 2019-12-14 10:36:56 UTC+0000                                 
0xfffffa800105c060 WmiPrvSE.exe           2636    588     12      293      0      0 2019-12-14 10:37:02 UTC+0000                                 
0xfffffa800100c060 WmiApSrv.exe           2004    484      6      115      0      0 2019-12-14 10:37:05 UTC+0000                                 
0xfffffa800230eb30 chrome.exe             1632   2296     14      219      2      0 2019-12-14 10:37:12 UTC+0000                                 
0xfffffa800101e640 dllhost.exe            2376    588      9      250      1      0 2019-12-14 10:37:40 UTC+0000                                 
0xfffffa800224a8c0 KeePass.exe            3008   1064     12      316      1      0 2019-12-14 10:37:56 UTC+0000                                 
0xfffffa8002230b30 sppsvc.exe             2764    484      5      151      0      0 2019-12-14 10:38:00 UTC+0000                                 
0xfffffa80010e5b30 svchost.exe            1076    484     17      337      0      0 2019-12-14 10:38:02 UTC+0000                                 
0xfffffa80010f44a0 wmpnetwk.exe            928    484     18      523      0      0 2019-12-14 10:38:03 UTC+0000                                 
0xfffffa80011956a0 notepad.exe            3260   3180      1       61      1      0 2019-12-14 10:38:20 UTC+0000                                 
0xfffffa80011aa060 DumpIt.exe             3844   1064      2       45      1      1 2019-12-14 10:38:43 UTC+0000                                 
0xfffffa8001194570 conhost.exe            3852    368      2       52      1      0 2019-12-14 10:38:43 UTC+0000                                 
0xfffffa8001189b30 WmiPrvSE.exe           4004    588      9  1572864 ------      0 2019-12-14 10:39:00 UTC+0000                                 
```

ones of interest are:
1. cmd.exe
2. chrome.exe
3. KeePass.exe

## solution
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/17536953-282b-4296-8616-2fd48df33bd5)  
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/4068fdd0-9aee-49ef-aeae-6d922f58c571)  
``ZmxhZ3t3M2xjMG0zX1QwXyRUNGczXyFfT2ZfTDRCXzJ9``  
using https://www.dcode.fr/cipher-identifier  
``flag{w3lc0m3_T0_$T4g3_!_Of_L4B_2}``  

now we will go through chrome.exe  
``volatility -f MemoryDump_Lab2.raw --profile=Win7SP1x64 filescan > filescan.txt head filescan.txt``  
``grep '\\Chrome\\User Data\\Default\\History' filescan.txt``  
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/413fbacd-e142-4dc8-bcd3-645a219cd7c9)  
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/da8fc56f-00c5-4db0-9d00-47001d12bde3)  
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/8d67f411-0f9a-4f67-9759-75040c23fc47)  
the zip file requires a password which is sha1sum of the flag for the lab1 challenge. ``sha1sum`` can be used.  

![image](https://github.com/Azure9733/Cryptonite/assets/143328010/5bcd27b5-1107-4e74-a87e-0f1da88ee346)  
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/a5933873-1edf-4406-a229-48799e9962db)  
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/624c5150-d743-4a1c-939c-3f5739fe2afa)  
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/f5bf4598-74fb-460b-b4c1-ba762b588ff7)  
![lab02-12](https://github.com/Azure9733/Cryptonite/assets/143328010/f38ac368-9e6b-4310-afd7-2d7a178f1e3a)  
