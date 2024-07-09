## Task 1: Container Management

1. List Containers:
```docker ps -a```
```sh
CONTAINER ID   IMAGE             COMMAND               CREATED        STATUS                       PORTS                                           NAMES
de50cd9b56de   goresumeapi:dev   "tail -f /dev/null"   18 hours ago   Exited (255) 2 minutes ago   0.0.0.0:32768->80/tcp, 0.0.0.0:32769->443/tcp   GOResume.API
```
2. Pull Latest Ubuntu Image:
```docker pull ubuntu:latest ```

```sh
latest: Pulling from library/ubuntu
9c704ecd0c69: Pull complete
Digest: sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest
```

3. Run Container:
```docker run -it --name ubuntu_container ubuntu:latest ```
``` sh
PS E:\VSandAS\VisualStudioProjects\lab1,2> docker run -it --name ubuntu_container ubuntu:latest
root@25058fec2029:/# 
```

4. Remove Image:
```docker rmi ubuntu:latest```
```sh
Untagged: ubuntu:latest
Untagged: ubuntu@sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Deleted: sha256:35a88802559dd2077e584394471ddaa1a2c5bfd16893b829ea57619301eb3908
Deleted: sha256:a30a5965a4f7d9d5ff76a46eb8939f58e95be844de1ac4a4b452d5d31158fdea
```