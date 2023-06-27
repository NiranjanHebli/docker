
### Set WebServer inside Docker


1) Launch linux OS and install dependencies

```
sudo su -
yum install docker -y
systemctl start docker 
systemctl enable docker 
```


2) Run the container in which you wish to run WebServer

```
docker run -it --name myweb centos:7
```

3) Check all the processes in the Base OS and Container,you would notice that Container has only 2 processes which doesnt include __systemd__.You can check this using Command

```
ps -aux
```

4) install dependencies inside container


```
yum install net-tools -y
yum install httpd -y
```

5) Navigate to directory inside container and activate bin 


```
cd /var/www/html
/usr/sbin/httpd
```

6) You can commit this image to use later in the Base OS

```
docker commit myweb myweb:v1
```

7) Use this image to run in the Base OS 

```
docker run -dit myweb:v1 httpd -DFOREGROUND
```

8) To do de-netting as well

```
docker run -d -it -p 1234:80 --name mywebcon myweb:v1 httpd -DFOREGROUND
```