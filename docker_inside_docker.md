
### Docker inside Docker


1) Launch AWS linux instance  and install dependencies

```
sudo su -
yum install docker -y
systemctl start docker 
systemctl enable docker 

```

2) Pull Docker Image 

```
 docker pull docker
```

3) Run image in privileged  mode

```
docker run --privileged -d --name mydocker docker:dind
```

4) Check that image is running 

```
docker ps
```

5) Run image of any OS inside the given image container

```
docker exec -it mydocker docker run -it --name myos centos:7
```

This way you can run docker container inside docker
(This is not the good practice but can be used for working on small data)
