###### **_ DWSCLASS - OPS - 005 - DOCKER _**

**Work with docker && containers.** 
 
 **__________________________**
 
## **Question 1:**
 1 - What signal is sent when the container is stoped by kill command?

Answer:
```
 1 - sigkill (The main process inside the container will be sent SIGKILL)
```

**__________________________**

## **Question 2:**
 1 - Create an alpine container, install nginx on it and then create another image.


Answer:
```
1 - docker run -tid --name alpine-nginx alpine #Create container
2 - docker exec -it alpine-nginx apk update    #update packages
3 - docker exec -it alpine-nginx apk add nginx #install nginx
4 - docker commit alpine-nginx alpine:nginx-test
5 - docker images | grep alpine:nginx-test

```

**__________________________**


## **Question 3:**
 1 - What happen for container processes when it become pause?

Answer:
```
1 - When a container become pause its cpu usages stops. container is on Ram but it does not have CPU.

```

**__________________________**

## **Question 4:**
 1 - Run a redis based container and put it's id on myredis.cid file

Answer:
```
1 - docker run -itd --name redis-cid --cidfile myredis.cid redis
```

**__________________________**

## **Question 5:**
 1 - Run a container based on following conditions:

    a - image           = nginx

    b - CPU             = 1.5 core

    c - memory          = 512M

    d - swap            = 256M

    e - cpu core number = 0


Answer:
```
1 -  docker run -idt --name test --memory 512M --memory-swap 768M --cpu-period 100000 --cpu-quota 150000 --cpuset-cpus 0  alpine 
```

**__________________________**

## **Question 6:**
 1 - Run a container based on following conditions:

    a - set environments:

       a.1 - CLASS     = nginx

       a.2 - NAME      = ali

    
Answer:
```
1 - docker run --name env_vars -itd -e CLASS=dws -e NAME=ali alpine
2 - docker exec -it env_vars env 

```

**Result:** = 
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
HOSTNAME=1ecd913a973a
TERM=xterm
CLASS=dws
NAME=ali
HOME=/root


**__________________________**

## **Question 7:**
 1 - Run a container based on following conditions:

    a - set /data to workdir
    
    b - mount an arbitrary path to /data
    
Answer:
```
1 - docker run --name alpine-storage -tid -v $PWD/projects/volumes/data:/data --workdir /data alpine

```