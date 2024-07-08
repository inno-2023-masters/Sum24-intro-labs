# Lab 7: Containers Lab - Docker
## Anton Buguev, a.buguev@innopolis.university, M23-RO-01

### Task 1. Container management.

1. List containers
```sh
$ docker ps -a

CONTAINER ID   IMAGE         COMMAND    CREATED         STATUS                     PORTS     NAMES
62e22b20bbb3   hello-world   "/hello"   24 minutes ago   Exited (0) 24 minutes ago             nifty_sanderson
```

2. Pull latest Ubuntu image
```sh
$ docker pull ubuntu:latest

latest: Pulling from library/ubuntu
9c704ecd0c69: Pull complete 
Digest: sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest
```

3. Run container
```sh
$ docker run -it --name ubuntu_container ubuntu:latest

root@38e1eb4b2803:/# 
```

Check running containers in different terminal:
```sh
$ docker ps -a

CONTAINER ID   IMAGE           COMMAND       CREATED         STATUS                     PORTS     NAMES
38e1eb4b2803   ubuntu:latest   "/bin/bash"   14 seconds ago   Up 13 seconds                         ubuntu_container
62e22b20bbb3   hello-world     "/hello"      25 minutes ago   Exited (0) 25 minutes ago             nifty_sanderson
```

4. Remove image
```sh
$ docker rmi ubuntu:latest

Error response from daemon: conflict: unable to remove repository reference "ubuntu:latest" (must force) - container 38e1eb4b2803 is using its referenced image 35a88802559d
```
Removing container failed.

