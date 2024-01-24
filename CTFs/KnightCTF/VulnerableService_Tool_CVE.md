# Vulnerable Service
## Challenge 
What service was vulnerable to the main server?  

Please use the attachment of the first challenge.  

Flag Format: KCTF{service_version} >>all_lower_case  
## Approach  
This time i genuinely had no clue how to do this.  
I decided to go through the packer captures and get an idea of the basic Structure.  
It seems, after the nikto scanner was run it basically ran all sorts of different tests. Almost all of the resulted in errors like 404.  
Quickly going through all the errors i came across the first packet that gave a response.  
When i opened that packet I found the name of the vulnerability.  
Ofcourse i confirmed it online and it was Part of Metasploit.  
Flag: ``KCTF{vsftpd_2.3.4}``  

Disclaimer: This is actually frustrating. I found the vulnerability in vsFTPd_2.3.4 format. I gave it as the answer and got it incorrect. I thought I was wrong so i kept trying to find other vulnerabilities. Then my teamate Alias [Ayush] said he was able to solve it (although he did it in a different manner) and sent me the flag. The only thing i did wrong was that the answer format was supposed to me in lower case only!!! They later edited the challenge and mentioned it.

# Famous Tool 
## Challenge
The attacker used a popular tool to gain access of the server. Can you name it?   
## Approach  
While i was confirmed the vsFTPd vulnerability, I ended up finding out that the Tool Metasploit is used to exploit it and indeed that was the correct answer.  
Flag: ``KCTF{metasploit}`` 
# CVE ID  
## Challenge  
What's the CVE id for the vulnerable service?  

Please use the attachment of the first challenge.  

Flag Format: KCTF{CVE-xxxx-xxxx}  
## Approach 
Just looked up the CVE ID for the vulnerability  
https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2011-2523  
Flag: ``KCTF{CVE-2011-2523}``
