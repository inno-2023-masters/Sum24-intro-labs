# Task 1

## List Containers:
```shell
aslan@aslan-X756UXM:~$ docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```
## Pull Latest Ubuntu Image:
```shell
aslan@aslan-X756UXM:~$ docker pull ubuntu:latest 
latest: Pulling from library/ubuntu
9c704ecd0c69: Pull complete 
Digest: sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest

What's Next?
  1. Sign in to your Docker account → docker login
  2. View a summary of image vulnerabilities and recommendations → docker scout quickview ubuntu:latest
```
## Run Container:
```shell
aslan@aslan-X756UXM:~$ docker run -it --name 9c704ecd0c69 ubuntu:latest 
root@98674570c98e:/# ls
bin   dev  home  lib64  mnt  proc  run   srv  tmp  var
boot  etc  lib   media  opt  root  sbin  sys  usr
root@98674570c98e:/# 
```
## Remove Image:
```shell
root@98674570c98e:/# exit
exit
```
```shell
aslan@aslan-X756UXM:~$ docker rmi ubuntu:latest 
Error response from daemon: conflict: unable to remove repository reference "ubuntu:latest" (must force) - container 98674570c98e is using its referenced image 35a88802559d

aslan@aslan-X756UXM:~$ docker stop 98674570c98e
98674570c98e

aslan@aslan-X756UXM:~$ docker rm 98674570c98e
98674570c98e

aslan@aslan-X756UXM:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

```

# Task 2