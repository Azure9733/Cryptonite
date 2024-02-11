## Funny Login

Approach:  
After downloading and extracting the file, i went through the source code.  
Tried different methods for SQL injection like ``' or '1'='1``  
Thought of possible ways to bruteforce although that plan failed miserably.  
entered parts of the code into gpt to understand their function.  
The application is generating 100,000 records of randomly-generated UUID and password and randomly selects one of them as admin.  

Post event writeup: https://ouuan.moe/post/2024/02/dicectf-2024-quals#funnylogin  
https://auk0x01.github.io/posts/DiceCTF2024-funnylogin-Writeup/  
so the injection was using ``pass="' UNION SELECT '1"``  
