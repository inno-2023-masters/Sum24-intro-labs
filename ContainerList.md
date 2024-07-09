# Task 1

1. List Containers:
```bash
PS C:\Users\ku_ku\Desktop\DEVOPS> docker ps -a
CONTAINER ID   IMAGE           COMMAND                  CREATED       STATUS                        PORTS                                                                                        NAMES
659179f0707a   ipfs/go-ipfs    "/sbin/tini -- /usr/…"   2 weeks ago   Exited (255) 2 weeks ago      0.0.0.0:4001->4001/tcp, 0.0.0.0:5001->5001/tcp, 4001/udp, 0.0.0.0:8080->8080/tcp, 8081/tcp   ipfs_host
a2118ee6ef3c   postgres:15.7   "docker-entrypoint.s…"   3 weeks ago   Exited (255) 52 seconds ago   0.0.0.0:5433->5432/tcp                                                                       lbs-server-db-1
```

2. Pull Latest Ubuntu Image:
```bash
PS C:\Users\ku_ku\Desktop\DEVOPS> docker pull ubuntu:latest
latest: Pulling from library/ubuntu
9c704ecd0c69: Pull complete
Digest: sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest

What is Next?
  View a summary of image vulnerabilities and recommendations → docker scout quickview ubuntu:latest
```

3. Run Container:
```bash
PS C:\Users\ku_ku\Desktop\DEVOPS> docker run -it --name ubuntu_container ubuntu:latest
root@dc204351b4c7:/# 
```

5. Remove Image:
```bash
PS C:\Users\ku_ku\Desktop\DEVOPS> docker rmi ubuntu:latest
Error response from daemon: conflict: unable to remove repository reference "ubuntu:latest" (must force) - container dc204351b4c7 is using its referenced image 35a88802559d
PS C:\Users\ku_ku\Desktop\DEVOPS> docker down dc204351b4c7
docker: 'down' is not a docker command.
See 'docker --help'
PS C:\Users\ku_ku\Desktop\DEVOPS> docker rm dc204351b4c7  
dc204351b4c7
PS C:\Users\ku_ku\Desktop\DEVOPS> docker rmi ubuntu:latest
Untagged: ubuntu:latest
Untagged: ubuntu@sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Deleted: sha256:35a88802559dd2077e584394471ddaa1a2c5bfd16893b829ea57619301eb3908
Deleted: sha256:a30a5965a4f7d9d5ff76a46eb8939f58e95be844de1ac4a4b452d5d31158fdea
```

1. **docker ps -a**:
    - Command: docker ps -a
    - Description: This command lists all containers, both running and stopped, on your system.
    - Option:
        - -a: Shows all containers (including stopped ones).

2. **docker pull ubuntu:latest**:
    - Command: docker pull ubuntu:latest
    - Description: This command pulls the latest version of the Ubuntu image from Docker Hub to your local machine.
    - Arguments:
        - ubuntu:latest: Specifies the image name (ubuntu) and tag (latest).

3. **docker run -it --name ubuntu_container ubuntu:latest**:
    - Command: docker run -it --name ubuntu_container ubuntu:latest
    - Description: This command creates and starts a new container based on the Ubuntu image with an interactive terminal.
    - Options:
        - -it: Allocates a pseudo-TTY and keeps STDIN open even if not attached.
        - --name ubuntu_container: Names the container as ubuntu_container.
        - ubuntu:latest: Specifies the image to use (ubuntu with tag latest).

4. **docker rmi ubuntu:latest**:
    - Command: docker rmi ubuntu:latest
    - Description: This command removes the specified image (ubuntu:latest) from your local Docker environment.
    - Argument:
        - ubuntu:latest: Specifies the image name (ubuntu) and tag (latest) to be removed.
