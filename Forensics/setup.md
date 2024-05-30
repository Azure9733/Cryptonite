I did not want to install volatility 2 so i used a Dockerfile to use volatility inside a container.  
Maybe i will change my ways if i face any significant issues.  
``cd /Downloads``  
``sudo docker build -t vol2``  
``sudo docker run -it vol2``  
should put you into root@some identifier value:~#  
``find / | grep -i vol.py``  
you should see a ``/root/vol/vol.py``  
``cd /root/vol/``  
then ``python2 vol.py``  
``volatility -h``  


Now that you have a docker container inside which youll do all the tasks, you might have to mount your downloads or document folder to the container for having access to the forensics files.  
so lets say for me its in my Documents folder  
``/home/kali/Documents``  
``sudo docker run -v /home/kali/Documents:/mnt/documents -it vol2``  
then once youre inside docker  
``cd /mnt/documents``  
should be there  
