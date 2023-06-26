

### Use Netcat to connect to the Docker container from another machine and send a message.


1) Open AWS console and launch an instance

2) Install Dependencies and enable docker 

```
sudo su -
yum install docker -y
systemctl start docker 
systemctl enable docker 

```

3) Expose docker image's  port 

```
docker run -p 8080:8080 centos:7 
```

4) Create a container in docker , run it 
and install dependencies

```
docker run -dit --name myos centos:7
docker attach myos
yum install net-tool -y
yum install nc -y  
```

5) Get ipaddress of container and note it down.

```
ifconfig
```

6) listen from __Docker Container__

```
nc -l 8080
```

7) Connect from __Local Machine__ ( Or AWS console)

``` 
nc [IP ADDRESS OF CONTAINER] 8080
```

Now you can send message between docker container and another machine
