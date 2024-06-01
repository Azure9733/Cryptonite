## Description
A malicious script encrypted a very secret piece of information I had on my system. Can you recover the information for me please?

**Note-1**: This challenge is composed of only 1 flag. The flag split into 2 parts.

**Note-2**: You'll need the first half of the flag to get the second.

You will need this additional tool to solve the challenge,

```bash
$ sudo apt install steghide
```

The flag format for this lab is: **inctf{s0me_l33t_Str1ng}**
## Clues
1. We need to look for a script in the memory dump.
2. using steg we are supposed to find something from a file.

## Solution
```
root@a0a6c5d849e3:/mnt/documents/memlabs/lab3# volatility -f MemoryDump_Lab3.raw --profile=Win7SP1x86_23418 pslist
Volatility Foundation Volatility Framework 2.6
Offset(V)  Name                    PID   PPID   Thds     Hnds   Sess  Wow64 Start                          Exit                          
---------- -------------------- ------ ------ ------ -------- ------ ------ ------------------------------ ------------------------------
0x83d09c60 System                    4      0     88      541 ------      0 2018-09-30 08:09:59 UTC+0000                                 
0x84551b98 smss.exe                260      4      2       29 ------      0 2018-09-30 08:09:59 UTC+0000                                 
0x84d58030 csrss.exe               340    332      9      352      0      0 2018-09-30 08:10:04 UTC+0000                                 
0x84d76030 csrss.exe               380    372     10      189      1      0 2018-09-30 08:10:05 UTC+0000                                 
0x84d77d28 wininit.exe             388    332      3       83      0      0 2018-09-30 08:10:05 UTC+0000                                 
0x84da6d28 winlogon.exe            424    372      3      115      1      0 2018-09-30 08:10:05 UTC+0000                                 
0x84dcdbd0 services.exe            484    388      6      195      0      0 2018-09-30 08:10:07 UTC+0000                                 
0x84dd0658 lsass.exe               492    388      6      561      0      0 2018-09-30 08:10:08 UTC+0000                                 
0x84dd4b28 lsm.exe                 500    388     10      151      0      0 2018-09-30 08:10:08 UTC+0000                                 
0x8454e348 svchost.exe             588    484     10      351      0      0 2018-09-30 08:10:12 UTC+0000                                 
0x84e15d28 VBoxService.ex          648    484     12      115      0      0 2018-09-30 08:10:13 UTC+0000                                 
0x84e1d030 svchost.exe             712    484      8      268      0      0 2018-09-30 08:10:14 UTC+0000                                 
0x84e5ad28 svchost.exe             800    484     18      438      0      0 2018-09-30 08:10:14 UTC+0000                                 
0x84e67d28 svchost.exe             852    484     16      371      0      0 2018-09-30 08:10:15 UTC+0000                                 
0x84e6b030 svchost.exe             880    484     18      452      0      0 2018-09-30 08:10:15 UTC+0000                                 
0x84e6fa18 svchost.exe             904    484     31     1116      0      0 2018-09-30 08:10:15 UTC+0000                                 
0x8481bcb0 svchost.exe            1236    484     15      478      0      0 2018-09-30 08:10:22 UTC+0000                                 
0x8484a800 spoolsv.exe            1340    484     12      285      0      0 2018-09-30 08:10:24 UTC+0000                                 
0x8485b030 svchost.exe            1368    484     18      302      0      0 2018-09-30 08:10:24 UTC+0000                                 
0x8488e860 svchost.exe            1488    484     11      267      0      0 2018-09-30 08:10:26 UTC+0000                                 
0x84893030 svchost.exe            1516    484     12      215      0      0 2018-09-30 08:10:26 UTC+0000                                 
0x85192030 LogonUI.exe             876    388      5      152      0      0 2018-09-30 08:10:40 UTC+0000                                 
0x8515cae0 sppsvc.exe              292    484      6      153      0      0 2018-09-30 08:12:31 UTC+0000                                 
0x8514bbf0 svchost.exe             440    484     13      342      0      0 2018-09-30 08:12:32 UTC+0000                                 
0x84d69d00 SearchIndexer.         1184    484     15      724      0      0 2018-09-30 08:12:33 UTC+0000                                 
0x8441d7e0 taskhost.exe           4816    484      8      196      1      0 2018-09-30 09:28:32 UTC+0000                                 
0xa0b21170 dwm.exe                3028    852      3      186      1      0 2018-09-30 09:28:36 UTC+0000                                 
0x8449d890 explorer.exe           5300   5128     30      871      1      0 2018-09-30 09:28:36 UTC+0000                                 
0x851cdd28 VBoxTray.exe           3064   5300     14      154      1      0 2018-09-30 09:28:44 UTC+0000                                 
0x84d77868 wuauclt.exe            5644    904      3       86      1      0 2018-09-30 09:28:49 UTC+0000                                 
0x9c627d28 msiexec.exe            1016    484      7      345      0      0 2018-09-30 09:39:03 UTC+0000                                 
0xbc2d08a8 msiexec.exe            5652   1016      0 --------      1      0 2018-09-30 09:39:13 UTC+0000   2018-09-30 09:41:17 UTC+0000  
0xbc21b9f0 TrustedInstall         4724    484      4      139      0      0 2018-09-30 09:40:24 UTC+0000                                 
0x84489800 audiodg.exe            5996    800      4      120      0      0 2018-09-30 09:45:22 UTC+0000                                 
0x83fbba40 SearchProtocol         5748   1184      7      281      0      0 2018-09-30 09:45:32 UTC+0000                                 
0x84ead628 DumpIt.exe             4116   5300      2       37      1      0 2018-09-30 09:45:43 UTC+0000                                 
0x84e37498 conhost.exe            3176    380      2       51      1      0 2018-09-30 09:45:43 UTC+0000                                 
0x84700ab8 dllhost.exe            1008    588      8      225      1      0 2018-09-30 09:45:48 UTC+0000                                 
0x84ef6768 SearchFilterHo         4036   1184      5       97      0      0 2018-09-30 09:47:36 UTC+0000                                 
0x9c6b0970 notepad.exe            3736   5300      1       60      1      0 2018-09-30 09:47:49 UTC+0000                                 
0x8443d3c0 notepad.exe            3432   5300      1       60      1      0 2018-09-30 09:47:50 UTC+0000
```

```
root@a0a6c5d849e3:/mnt/documents/memlabs/lab3# volatility -f MemoryDump_Lab3.raw --profile=Win7SP1x86_23418 cmdline
Volatility Foundation Volatility Framework 2.6
************************************************************************
System pid:      4
************************************************************************
smss.exe pid:    260
Command line : \SystemRoot\System32\smss.exe
************************************************************************
csrss.exe pid:    340
Command line : %SystemRoot%\system32\csrss.exe ObjectDirectory=\Windows SharedSection=1024,12288,512 Windows=On SubSystemType=Windows ServerDll=basesrv,1 ServerDll=winsrv:UserServerDllInitialization,3 ServerDll=winsrv:ConServerDllInitialization,2 ServerDll=sxssrv,4 ProfileControl=Off MaxRequestThreads=16
************************************************************************
csrss.exe pid:    380
Command line : %SystemRoot%\system32\csrss.exe ObjectDirectory=\Windows SharedSection=1024,12288,512 Windows=On SubSystemType=Windows ServerDll=basesrv,1 ServerDll=winsrv:UserServerDllInitialization,3 ServerDll=winsrv:ConServerDllInitialization,2 ServerDll=sxssrv,4 ProfileControl=Off MaxRequestThreads=16
************************************************************************
wininit.exe pid:    388
Command line : wininit.exe
************************************************************************
winlogon.exe pid:    424
Command line : winlogon.exe
************************************************************************
services.exe pid:    484
Command line : C:\Windows\system32\services.exe
************************************************************************
lsass.exe pid:    492
Command line : C:\Windows\system32\lsass.exe
************************************************************************
lsm.exe pid:    500
Command line : C:\Windows\system32\lsm.exe
************************************************************************
svchost.exe pid:    588
Command line : C:\Windows\system32\svchost.exe -k DcomLaunch
************************************************************************
VBoxService.ex pid:    648
Command line : C:\Windows\System32\VBoxService.exe
************************************************************************
svchost.exe pid:    712
Command line : C:\Windows\system32\svchost.exe -k RPCSS
************************************************************************
svchost.exe pid:    800
Command line : C:\Windows\System32\svchost.exe -k LocalServiceNetworkRestricted
************************************************************************
svchost.exe pid:    852
Command line : C:\Windows\System32\svchost.exe -k LocalSystemNetworkRestricted
************************************************************************
svchost.exe pid:    880
Command line : C:\Windows\system32\svchost.exe -k LocalService
************************************************************************
svchost.exe pid:    904
Command line : C:\Windows\system32\svchost.exe -k netsvcs
************************************************************************
svchost.exe pid:   1236
Command line : C:\Windows\system32\svchost.exe -k NetworkService
************************************************************************
spoolsv.exe pid:   1340
Command line : C:\Windows\System32\spoolsv.exe
************************************************************************
svchost.exe pid:   1368
Command line : C:\Windows\system32\svchost.exe -k LocalServiceNoNetwork
************************************************************************
svchost.exe pid:   1488
Command line : C:\Windows\System32\svchost.exe -k utcsvc
************************************************************************
svchost.exe pid:   1516
Command line : C:\Windows\system32\svchost.exe -k LocalServiceAndNoImpersonation
************************************************************************
LogonUI.exe pid:    876
Command line : "LogonUI.exe" /flags:0x1
************************************************************************
sppsvc.exe pid:    292
Command line : C:\Windows\system32\sppsvc.exe
************************************************************************
svchost.exe pid:    440
Command line : C:\Windows\System32\svchost.exe -k secsvcs
************************************************************************
SearchIndexer. pid:   1184
Command line : C:\Windows\system32\SearchIndexer.exe /Embedding
************************************************************************
taskhost.exe pid:   4816
Command line : "taskhost.exe"
************************************************************************
dwm.exe pid:   3028
Command line : "C:\Windows\system32\Dwm.exe"
************************************************************************
explorer.exe pid:   5300
Command line : C:\Windows\Explorer.EXE
************************************************************************
VBoxTray.exe pid:   3064
Command line : "C:\Windows\System32\VBoxTray.exe" 
************************************************************************
wuauclt.exe pid:   5644
Command line : "C:\Windows\system32\wuauclt.exe"
************************************************************************
msiexec.exe pid:   1016
Command line : C:\Windows\system32\msiexec.exe /V
************************************************************************
msiexec.exe pid:   5652
************************************************************************
TrustedInstall pid:   4724
Command line : C:\Windows\servicing\TrustedInstaller.exe
************************************************************************
audiodg.exe pid:   5996
Command line : C:\Windows\system32\AUDIODG.EXE 0x830
************************************************************************
SearchProtocol pid:   5748
Command line : "C:\Windows\system32\SearchProtocolHost.exe" Global\UsGthrFltPipeMssGthrPipe7_ Global\UsGthrCtrlFltPipeMssGthrPipe7 1 -2147483646 "Software\Microsoft\Windows Search" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT; MS Search 4.0 Robot)" "C:\ProgramData\Microsoft\Search\Data\Temp\usgthrsvc" "DownLevelDaemon" 
************************************************************************
DumpIt.exe pid:   4116
Command line : "C:\Users\hello\Desktop\DumpIt\DumpIt.exe" 
************************************************************************
conhost.exe pid:   3176
Command line : \??\C:\Windows\system32\conhost.exe "-578845771-1540166818332419906-659764396-174055078882731463-1164958248-211768531
************************************************************************
dllhost.exe pid:   1008
Command line : C:\Windows\system32\DllHost.exe /Processid:{76D0CB12-7604-4048-B83C-1005C7DDC503}
************************************************************************
SearchFilterHo pid:   4036
Command line : "C:\Windows\system32\SearchFilterHost.exe" 0 512 516 524 65536 520 
************************************************************************
notepad.exe pid:   3736
Command line : "C:\Windows\system32\NOTEPAD.EXE" C:\Users\hello\Desktop\evilscript.py
************************************************************************
notepad.exe pid:   3432
Command line : "C:\Windows\system32\NOTEPAD.EXE" C:\Users\hello\Desktop\vip.txt
```
```
volatility -f MemoryDump_Lab3.raw --profile=Win7SP1x86_23418 filescan > filescan.txt
grep -E '\\Desktop\\evilscript.py|\\Desktop\\vip.txt' filescan.txt
volatility -f MemoryDump_Lab3.raw --profile=Win7SP1x86_23418 dumpfiles -Q 0x000000003de1b5f0 -D . -n
volatility -f MemoryDump_Lab3.raw --profile=Win7SP1x86_23418 dumpfiles -Q 0x000000003e727e50 -D . -n
```
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/0b4ef050-24f4-41c8-888a-1b4378bda2e5)   
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/5ca1fc72-9e97-42aa-9883-853562fed824)  
the script is XORing each character of a given string and encoding it to Base64.  
reversing it gives the first part of the flag  
```inctf{0n3_h4lf```
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/bdd100ce-3d10-408c-a82b-fcfbc0b4b123)  
using steghide extract, i get the second half of the flag  
``_1s_n0t_3n0ugh}``
