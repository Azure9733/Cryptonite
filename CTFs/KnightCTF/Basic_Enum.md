# Basic Enum  
## Challenge 
What tool did the attacker use to do basic enumeration of the server?  
Please use the attachment of the first challenge.  
Flag Format: KCTF{toolname}  
## Approach
I looked around the packets that handled the ``maybeconfidential.zip`` file but soon realised that I could not find the solution in this way. Moreover I did not really know when the vulnerability scanner was used.  
So I decided to go through the same method of exporting objects but this time I went through all the content. Soon I found the Application which was used to scan for vunerabilities.  
Here is the video of how i sovled it: https://cdn.discordapp.com/attachments/1198550053111996416/1198551057056411738/Basic_Enum.mp4?ex=65bf50a8&is=65acdba8&hm=5801438445da9a5aa72d6a00f8cac78b469cb3ad20d371ac984f8613701b6660&  
In order to confirm my suspicion i looked up nikto and indeed it was the web scanner.  
https://www.freecodecamp.org/news/an-introduction-to-web-server-scanning-with-nikto/  
Flag: ``KCTF{nikto}``  
