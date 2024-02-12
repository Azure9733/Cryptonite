## Wordpress 2
### Challenge:  
Q1. During enumeration, the attacker tried to identify users on the site. List all the users that the attacker enumerated. (seperate them with :),(sort them by alphapitical order)  

Q2. After enumeration, a brute force attack was launched against all users. The attacker successfully gained access to one of the accounts. What are the username and password for that account, and what is the name of the page used for the brute force attack?  

Flag Format 0xL4ugh{A1_A2}  

    Example: 0xL4ugh{username1:username2_username:password_pageName.ext}  
### Approach: 
There were various method of finding the users.  
The most convinient was using network miner, the credentials tab gave the usernames and their passwords.  
![image](https://github.com/Azure9733/Cryptonite/assets/143328010/eccb87c9-966d-4c6b-91b8-1b1c6a0237c3)  
The page used was ``xmlrpc.php``  

However finding the user with which there was a successful login was difficult.  
I tried some combinations like  
``0xL4ugh{a1l4m:not7amoksha_a1l4m:55806695_xmlrpc.php}  
0xL4ugh{a1l4m:not7amoksha_demomorgan:f69cd672_xmlrpc.php}  
0xL4ugh{a1l4m:not7amoksha_not7amoksha:7a4a1395_xmlrpc.php}``  
none of them worked.  
I used a python script on the packet capture file to extract the usernames called ``usernames.py``  

    from scapy.all import *
    def extract_usernames(fileIn):
    usernames = set()
    packets = rdpcap(fileIn)
  
    # Filter HTTP POST requests
    http_post_packets = [pkt for pkt in packets if pkt.haslayer(TCP) and pkt.haslayer(Raw) and b"POST" in pkt[Raw].load]

    # Extract usernames from POST requests
    for packet in http_post_packets:
        load = str(packet[Raw].load)
        if "POST" in load and "wp-login.php" in load:
            # Extract username parameter (adjust accordingly)
            username_index = load.find("log=") + 4
            end_index = load.find("&", username_index)
            username = load[username_index:end_index] if end_index != -1 else load[username_index:]
            usernames.add(username)

    return usernames

    # Usage example
    if __name__ == "__main__":
    packet_capture_file = "Wordpress.pcapng"
    extracted_usernames = extract_usernames(packet_capture_file)
    print("Extracted Usernames:")
    for username in extracted_usernames:
        print(username)  

![Screenshot 2024-02-10 192244](https://github.com/Azure9733/Cryptonite/assets/143328010/2e5b2d67-27b3-46d5-852a-e55c23928697)  
Now I tried more possible combinations:   
``0xL4ugh{a1l4m:demomorgan:not7amoksha_a1l4m:55806695_xmlrpc.php}  
0xL4ugh{a1l4m:demomorgan:not7amoksha_demomorgan:f69cd672_xmlrpc.php}  
0xL4ugh{a1l4m:demomorgan:not7amoksha_not7amoksha:7a4a1395_xmlrpc.php}``  
Something was still wrong.  
The password for demomorgan was actually demomorgan itself. This was proven by the following:-  

``` POST /wordpress/xmlrpc.php HTTP/1.1
Host: 192.168.204.128
Accept: */*
Accept-Encoding: gzip, deflate
Cookie: wordpress_test_cookie=WP%20Cookie%20check
User-Agent: WPScan v3.8.25 (https://wpscan.com/wordpress-security-scanner)
Referer: http://192.168.204.128/wordpress
Content-Length: 220
Content-Type: application/x-www-form-urlencoded
<?xml version="1.0" ?><methodCall><methodName>wp.getUsersBlogs</methodName><params><param><value><string>demomorgan</string></value></param><param><value><string>demomorgan</string></value></param></params></methodCall>
HTTP/1.1 200 OK
Date: Wed, 17 Jan 2024 21:55:19 GMT
Server: Apache/2.4.58 (Win64) OpenSSL/3.1.3 PHP/8.2.12
X-Powered-By: PHP/8.2.12
Connection: close
Content-Length: 669
Content-Type: text/xml; charset=UTF-8

<?xml version="1.0" encoding="UTF-8"?>
<methodResponse>
  <params>
    <param>
      <value>
      <array><data>
  <value><struct>
  <member><name>isAdmin</name><value><boolean>0</boolean></value></member>
  <member><name>url</name><value><string>http://192.168.204.128/wordpress/</string></value></member>
  <member><name>blogid</name><value><string>1</string></value></member>
  <member><name>blogName</name><value><string>0xL4ugh FTW</string></value></member>
  <member><name>xmlrpc</name><value><string>http://192.168.204.128/wordpress/xmlrpc.php</string></value></member>
</struct></value>
</data></array>
      </value>
    </param>
  </params>
</methodResponse>
```
Final Flag: ``0xL4ugh{a1l4m:demomorgan:not7amoksha_demomorgan:demomorgan_xmlrpc.php}``
