## Prerequisites
- `git clone https://github.com/CTFd/CTFd.git`  
- `cd CTFd`  
- `sudo apt install mariadb-server`
- `sudo systemctl start mariadb`
- `sudo service mysql start`
- `sudo systemctl status mariadb`
- Make sure docker is installed and **run in inside the CTFd directory**. **And always use docker with sudo.**
Install Docker and `docker compose` (this may vary in difficulty based on your linux distro)
`sudo apt-get install docker-compose-plugin` hopefully it did the job. If it was unable to locate the package, follow along.    
https://docs.docker.com/engine/install/debian/#install-using-the-repository  
follow the commands provided in the `Install using the apt repository` inside the above blog.  
IF after running `sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin` you get the following error:  
![333837948-792575c7-aad2-4fe9-89ca-317a261eae0f](https://github.com/user-attachments/assets/222f16ad-f662-4c96-b7bd-f14472df4b51)   
follow the following commands:  
1. `DOCKER_CONFIG=${DOCKER_CONFIG:-$HOME/.docker}`
2. `DOCKER_CONFIG=${DOCKER_CONFIG:-/usr/local/lib/docker}`
3. `mkdir -p $DOCKER_CONFIG/cli-plugins`
4. `curl -SL https://github.com/docker/compose/releases/download/v2.27.0/docker-compose-linux-x86_64 -o $DOCKER_CONFIG/cli-plugins/docker-compose`
5. `chmod +x $DOCKER_CONFIG/cli-plugins/docker-compose`  
`docker compose version`
6. `cd $DOCKER_CONFIG`  
![333839018-4279672d-ab76-4524-b3af-a5991e138448](https://github.com/user-attachments/assets/3a41396d-bfbe-471e-9d6c-0f334cd4c509)  
7. `sudo mkdir -p /usr/local/lib/docker/cli-plugins`
8. `curl -SL https://github.com/docker/compose/releases/download/v2.27.0/docker-compose-linux-x86_64 -o /usr/local/lib/docker/cli-plugins/docker-compose`
9. `sudo chmod +x /usr/local/lib/docker/cli-plugins/docker-compose`
10. `sudo docker compose version`  
![333839314-cd5a8523-1634-426c-aa87-b9d728ca3f1d](https://github.com/user-attachments/assets/9112c3f2-8bc8-4fb8-ace1-cf14b30d6130)  
11. `cd CTFd`
12. `sudo docker compose up` (it should start building)
- verify by running this if you want:`sudo docker run hello-world`  
![333837727-44376e27-e19f-4579-8ac3-6f3675d4639d](https://github.com/user-attachments/assets/b168cad0-8d17-461f-b542-d922fd7a0975)  
- Install docker compose not docker-compose (delete that shit).  
  `sudo apt remove docker-compose`



    Now you will need to change the docker-compose.yml file
Just look it up but here is my template to refer to so that you know what works
```
version: '3'

services:
  ctfd:
    build: .
    user: root
    restart: always
    ports:
      - "8000:8000"
    environment:
      - UPLOAD_FOLDER=/var/uploads
      - DATABASE_URL=mysql+pymysql://<USERNAME>:<PASSWORD>@<IP ADDRESS>:4200/ctfd_db
      - REDIS_URL=redis://cache:6379
      - WORKERS=1
      - LOG_FOLDER=/var/log/CTFd
      - ACCESS_LOG=-
      - ERROR_LOG=-
      - REVERSE_PROXY=true
    volumes:
      - .data/CTFd/logs:/var/log/CTFd
      - .data/CTFd/uploads:/var/uploads
      - .:/opt/CTFd:ro
    networks:
        default:
        internal:

  nginx:
    image: nginx:stable
    restart: always
    volumes:
      - ./conf/nginx/http.conf:/etc/nginx/nginx.conf
    ports:
      - "4873:8000"
    depends_on:
      - ctfd
    networks:
      - default
      - internal
  cache:
    image: redis:4
    restart: always
    volumes:
    - .data/redis:/data
    networks:
        internal:
networks:
    default:
    internal:
        internal: true
```
`sudo vim /etc/mysql/mariadb.conf.d/50-server.cnf`
You need to change the bind address to your host ip address
- ``ifconfig`` since i am using a vm, my host ip is the one in ethernet.
  - Check if the ip is active by ``ping 192.168.XX.XXX``  
![333867081-993fea0d-4b8a-4004-b72b-21e7e82ca5f7](https://github.com/user-attachments/assets/cb368b30-4ba4-4d2a-aee9-bcac73520e4b)  
  - ``sudo vim /etc/mysql/mariadb.conf.d/50-server.cnf``   
![333867149-bced78e5-8ef0-464b-9c32-0f876bd59a16](https://github.com/user-attachments/assets/ff810450-6891-4459-99a5-79212f30326d)  
Now just `sudo docker compose up`
