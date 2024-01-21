## Challenge  
In the mystical land of Eldoria, a fierce dragon had captured the kingdom's most precious treasure, hiding it behind a magical binary. The bravest knight of the realm, Sir Emeric, known for both sword and wit, embarked on a quest to retrieve the treasure. To succeed, he must reverse the dragon's binary. As Sir Emeric's trusted apprentice in "Dragon's Binary" you are tasked with solving the cipher to reveal the hidden treasure and help vanquish the dragon's spell. Your journey is filled with mystery and danger, where only the sharpest mind can prevail.  
Right Passcode is the flag. 
## Approach  
Disclaimer: I would like to mention that my team member Harshith was very helpful in solving this challenge. He taught me how to navigate Ghidra.  
I downloaded the zipped file and extracted it.  
Approach 1: The terminal way  
I used the strings command on the Dragon.Binary along with the head command and got the passcode.  
``strings Dragon.Binary | head -n 30``  
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/6a465a1d-e46c-4ed7-8dcb-3ba464b9722f)  
Approach 2: Open the binary program on Ghidra. 
Searched for Strings and got the flag.
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/35cbad7c-2a7b-4961-a3c6-33f18da466e1)  
Flag : ``letMeIn``
