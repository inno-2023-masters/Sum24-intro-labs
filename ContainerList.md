# Lab 8 Containers Lab - Docker

## Container Management

1. **List Containers**

Command: ``docker ps -a``
Output (local machine): 

```
CONTAINER ID   IMAGE             COMMAND               CREATED          STATUS          PORTS                                           NAMES
69950e02f242   goresumeapi:dev   "tail -f /dev/null"   25 minutes ago   Up 25 minutes   0.0.0.0:32769->80/tcp, 0.0.0.0:32768->443/tcp   GOResume.API_1
```
Output (server where is deployed Industrial Project):

```
root@dimoninbirsk:~# docker ps -a
CONTAINER ID   IMAGE             COMMAND                  CREATED        STATUS        PORTS                                                                    NAMES
6a55accf0624   backend           "dotnet GOResume.API…"   27 hours ago   Up 27 hours   0.0.0.0:82->80/tcp, :::82->80/tcp, 0.0.0.0:83->443/tcp, :::83->443/tcp   interesting_leavitt
b3b72658276c   frontend          "docker-entrypoint.s…"   4 days ago     Up 4 days     0.0.0.0:81->5173/tcp, :::81->5173/tcp                                    interesting_tesla
5f3a65dafe44   postgres:latest   "docker-entrypoint.s…"   6 weeks ago    Up 6 weeks    0.0.0.0:5433->5432/tcp, :::5433->5432/tcp                                postgres
```
2. **Pull Ubuntu Container**
```
C:\Users\dimoninbirsk>docker pull ubuntu:latest
latest: Pulling from library/ubuntu
9c704ecd0c69: Pull complete
Digest: sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest
```

3. **Run container**:

```
C:\Users\dimoninbirsk>docker run -it --name ubuntu_container ubuntu:latest
root@0bca5117d111:/# ls -a
.  ..  .dockerenv  bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@0bca5117d111:/#
```

As there is not ``-rm`` flag in command, I cannot just remove image. First I need to stop the container with ``docker stop ubuntu_container``, then remove container with ``docker rm ubuntu_container`` and only now I can remove image:

```
C:\Users\dimoninbirsk>docker rmi ubuntu:latest
Untagged: ubuntu:latest
Untagged: ubuntu@sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Deleted: sha256:35a88802559dd2077e584394471ddaa1a2c5bfd16893b829ea57619301eb3908
Deleted: sha256:a30a5965a4f7d9d5ff76a46eb8939f58e95be844de1ac4a4b452d5d31158fdea
```