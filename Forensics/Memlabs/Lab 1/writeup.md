## Challenge description
My sister's computer crashed. We were very fortunate to recover this memory dump. Your job is get all her important files from the system. From what we remember, we suddenly saw a black window pop up with some thing being executed. When the crash happened, she was trying to draw something. Thats all we remember from the time of crash.

Note: This challenge is composed of 3 flags.

## Clues
1. Need to get the important files  
2. a black popup is probably some commands being executed in the command like.
3. since she was trying to draw something, its probably ms paint or some other canvas editor.

## Initial Info
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/b2a90dcd-29e4-4f30-94d2-e314624408d4)  
```
root@a0a6c5d849e3:/mnt/documents/memlabs/lab1# volatility -f MemoryDump_Lab1.raw --profile=Win7SP1x64 pslist
Volatility Foundation Volatility Framework 2.6
Offset(V)          Name                    PID   PPID   Thds     Hnds   Sess  Wow64 Start                          Exit                          
------------------ -------------------- ------ ------ ------ -------- ------ ------ ------------------------------ ------------------------------
0xfffffa8000ca0040 System                    4      0     80      570 ------      0 2019-12-11 13:41:25 UTC+0000                                 
0xfffffa800148f040 smss.exe                248      4      3       37 ------      0 2019-12-11 13:41:25 UTC+0000                                 
0xfffffa800154f740 csrss.exe               320    312      9      457      0      0 2019-12-11 13:41:32 UTC+0000                                 
0xfffffa8000ca81e0 csrss.exe               368    360      7      199      1      0 2019-12-11 13:41:33 UTC+0000                                 
0xfffffa8001c45060 psxss.exe               376    248     18      786      0      0 2019-12-11 13:41:33 UTC+0000                                 
0xfffffa8001c5f060 winlogon.exe            416    360      4      118      1      0 2019-12-11 13:41:34 UTC+0000                                 
0xfffffa8001c5f630 wininit.exe             424    312      3       75      0      0 2019-12-11 13:41:34 UTC+0000                                 
0xfffffa8001c98530 services.exe            484    424     13      219      0      0 2019-12-11 13:41:35 UTC+0000                                 
0xfffffa8001ca0580 lsass.exe               492    424      9      764      0      0 2019-12-11 13:41:35 UTC+0000                                 
0xfffffa8001ca4b30 lsm.exe                 500    424     11      185      0      0 2019-12-11 13:41:35 UTC+0000                                 
0xfffffa8001cf4b30 svchost.exe             588    484     11      358      0      0 2019-12-11 13:41:39 UTC+0000                                 
0xfffffa8001d327c0 VBoxService.ex          652    484     13      137      0      0 2019-12-11 13:41:40 UTC+0000                                 
0xfffffa8001d49b30 svchost.exe             720    484      8      279      0      0 2019-12-11 13:41:41 UTC+0000                                 
0xfffffa8001d8c420 svchost.exe             816    484     23      569      0      0 2019-12-11 13:41:42 UTC+0000                                 
0xfffffa8001da5b30 svchost.exe             852    484     28      542      0      0 2019-12-11 13:41:43 UTC+0000                                 
0xfffffa8001da96c0 svchost.exe             876    484     32      941      0      0 2019-12-11 13:41:43 UTC+0000                                 
0xfffffa8001e1bb30 svchost.exe             472    484     19      476      0      0 2019-12-11 13:41:47 UTC+0000                                 
0xfffffa8001e50b30 svchost.exe            1044    484     14      366      0      0 2019-12-11 13:41:48 UTC+0000                                 
0xfffffa8001eba230 spoolsv.exe            1208    484     13      282      0      0 2019-12-11 13:41:51 UTC+0000                                 
0xfffffa8001eda060 svchost.exe            1248    484     19      313      0      0 2019-12-11 13:41:52 UTC+0000                                 
0xfffffa8001f58890 svchost.exe            1372    484     22      295      0      0 2019-12-11 13:41:54 UTC+0000                                 
0xfffffa8001f91b30 TCPSVCS.EXE            1416    484      4       97      0      0 2019-12-11 13:41:55 UTC+0000                                 
0xfffffa8000d3c400 sppsvc.exe             1508    484      4      141      0      0 2019-12-11 14:16:06 UTC+0000                                 
0xfffffa8001c38580 svchost.exe             948    484     13      322      0      0 2019-12-11 14:16:07 UTC+0000                                 
0xfffffa8002170630 wmpnetwk.exe           1856    484     16      451      0      0 2019-12-11 14:16:08 UTC+0000                                 
0xfffffa8001d376f0 SearchIndexer.          480    484     14      701      0      0 2019-12-11 14:16:09 UTC+0000                                 
0xfffffa8001eb47f0 taskhost.exe            296    484      8      151      1      0 2019-12-11 14:32:24 UTC+0000                                 
0xfffffa8001dfa910 dwm.exe                1988    852      5       72      1      0 2019-12-11 14:32:25 UTC+0000                                 
0xfffffa8002046960 explorer.exe            604   2016     33      927      1      0 2019-12-11 14:32:25 UTC+0000                                 
0xfffffa80021c75d0 VBoxTray.exe           1844    604     11      140      1      0 2019-12-11 14:32:35 UTC+0000                                 
0xfffffa80021da060 audiodg.exe            2064    816      6      131      0      0 2019-12-11 14:32:37 UTC+0000                                 
0xfffffa80022199e0 svchost.exe            2368    484      9      365      0      0 2019-12-11 14:32:51 UTC+0000                                 
0xfffffa8002222780 cmd.exe                1984    604      1       21      1      0 2019-12-11 14:34:54 UTC+0000                                 
0xfffffa8002227140 conhost.exe            2692    368      2       50      1      0 2019-12-11 14:34:54 UTC+0000                                 
0xfffffa80022bab30 mspaint.exe            2424    604      6      128      1      0 2019-12-11 14:35:14 UTC+0000                                 
0xfffffa8000eac770 svchost.exe            2660    484      6      100      0      0 2019-12-11 14:35:14 UTC+0000                                 
0xfffffa8001e68060 csrss.exe              2760   2680      7      172      2      0 2019-12-11 14:37:05 UTC+0000                                 
0xfffffa8000ecbb30 winlogon.exe           2808   2680      4      119      2      0 2019-12-11 14:37:05 UTC+0000                                 
0xfffffa8000f3aab0 taskhost.exe           2908    484      9      158      2      0 2019-12-11 14:37:13 UTC+0000                                 
0xfffffa8000f4db30 dwm.exe                3004    852      5       72      2      0 2019-12-11 14:37:14 UTC+0000                                 
0xfffffa8000f4c670 explorer.exe           2504   3000     34      825      2      0 2019-12-11 14:37:14 UTC+0000                                 
0xfffffa8000f9a4e0 VBoxTray.exe           2304   2504     14      144      2      0 2019-12-11 14:37:14 UTC+0000                                 
0xfffffa8000fff630 SearchProtocol         2524    480      7      226      2      0 2019-12-11 14:37:21 UTC+0000                                 
0xfffffa8000ecea60 SearchFilterHo         1720    480      5       90      0      0 2019-12-11 14:37:21 UTC+0000                                 
0xfffffa8001010b30 WinRAR.exe             1512   2504      6      207      2      0 2019-12-11 14:37:23 UTC+0000                                 
0xfffffa8001020b30 SearchProtocol         2868    480      8      279      0      0 2019-12-11 14:37:23 UTC+0000                                 
0xfffffa8001048060 DumpIt.exe              796    604      2       45      1      1 2019-12-11 14:37:54 UTC+0000                                 
0xfffffa800104a780 conhost.exe            2260    368      2       50      1      0 2019-12-11 14:37:54 UTC+0000
```
Processes can be classiefied into:
- System Processes (mostly unsuspicious but sometimes malicious proocesses could try to hide as system processes)
  1. System (PID 4)
  2. smss.exe (Session Manager Subsystem)
  3. csrss.exe (Client/Server Runtime Subsystem)
  4. psxss.exe (Windows Process Status Helper service)
  5. winlogon.exe (Windows Logon Application)
  6. wininit.exe (Windows Initialization Process)
  7. services.exe (Services and Controller app)
  8. lsass.exe (Local Security Authority Subsystem Service)
  9. lsm.exe (Local Session Manager Service)
  10. svchost.exe (Service Host Process)
  11. spoolsv.exe (Spooler SubSystem App aka printing service)
  12. TCPSVCS.EXE (TCP/IP Services Application)
  13. sppsvc.exe (Software Protection Platform Service)
  14. wmpnetwk.exe (Windows Media Player Network Sharing Service)
  15. SearchIndexer.exe (Windows Search Indexer service)
  16. taskhost.exe (Task Manager)
  17. dwm.exe (Desktop Window Manager)
  18. explorer.exe (Windows Explorer - Taskbar, File manager, Icons)
  19. audiodg.exe (Windows Audio Device Graph Isolation)
  21. conhost.exe (Console Window Host)
  22. SearchProtocolHost.exe (Windows Search protocol handler)
  23. SearchFilterHost.exe (Windows Search functionality)

- User Processes
  1. VBoxService.ex (VirtualBox Guest Additions Service)
  2. VBoxTray.exe (Associated with VirtualBox Guest Additions Service)
  3. cmd.exe (Command Prompt)
  4. mspaint.exe (Microsoft Paint)
  5. WinRAR.exe (WinRAR)
  6. DumpIt.exe (Memory Acquisition Tool)
- Clearly, I will focus on cmd.exe, mspaint.exe and WinRAR.exe.
 ## Solution
 ![image](https://github.com/Azure9733/Cryptonite/assets/143328010/c38fee93-e8a4-4f81-8eec-5e11f8099d9e)  
St4G3$1 is a weird command. Checking its Pid: 2692
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/a2483019-1718-451b-b0e1-116efae0b78c)  
``ZmxhZ3t0aDFzXzFzX3RoM18xc3Rfc3Q0ZzMhIX0=`` is base64 output
decoded: ``'flag{th1s_1s_th3_1st_st4g3!!}'`` 
Next is mspaint.  
I do memdump on the ms paint process.  
To extract images from raw data, the following blog was referred.  
https://w00tsec.blogspot.com/2015/02/extracting-raw-pictures-from-memory.html  
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/31c8a6cb-2686-418d-ae13-c87d45aaf498)  
``flag{G00d_BoY_good_girL}``
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/c145bbe7-5439-4306-a4a7-eeb9f6cb6ea7)  
Important.rar must be the important files.  
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/897f0777-d475-4210-870e-fa70b219f3db)  
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/a047eea7-b3ac-4f34-9604-70138184333d) 
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/b5a27164-adb7-4f2b-af9a-c56e3ff3e6ae)  
``F4FF64C8BAAC57D22F22EDC681055BA6``
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/146cb8ba-767e-4dc3-9d50-ebad72346070)  
