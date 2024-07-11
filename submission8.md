# Task 1: Container Management

## 1. List Containers

Use the following command to list all Docker containers, including the ones that are stopped:

`docker ps -a`

```sh
C:\Windows\System32>docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED       STATUS                   PORTS     NAMES
52ee8f239977   ipfs/go-ipfs   "/sbin/tini -- /usr/…"   3 weeks ago   Exited (0) 3 weeks ago             ipfs_host
```

## 2. Pull Latest Ubuntu Image

Use the following command to pull the latest Ubuntu image from the Docker registry:

`docker pull ubuntu:latest`

```sh
C:\Windows\System32>docker pull ubuntu:latest
latest: Pulling from library/ubuntu
9c704ecd0c69: Pull complete
Digest: sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest
```

## 3. Run Container

Use the following command to run a container using the Ubuntu image you just pulled:

`docker run -it --name ubuntu_container ubuntu:latest`

![Ubuntu Image](/media/ubuntuImage.png)

## 4. Remove Image

Attempt to remove the Ubuntu image you pulled earlier:

`docker rmi ubuntu:latest`

```sh
C:\Windows\System32>docker rmi ubuntu:latest
Error response from daemon: conflict: unable to remove repository reference "ubuntu:latest" (must force) - container b4cb83f9769b is using its referenced image 35a88802559d
```

Solution is to remoove container firstly then remoovin image:
![Remooving Ubuntu Image](/media/remoovingImage.png)

# Task 2: Image and Container Operations

## 1. Create Image Archive

First, pull the latest Ubuntu image because we remoove it before:

`docker pull ubuntu:latest`

Then create an archive file from it:

`docker save -o ubuntu_image.tar ubuntu:latest`

## 2. Run Nginx Container

Use the following command to run a container using the Nginx web server image. Bind the container's port 80 to the local port 80, run the container in detached mode, and name it nginx_container:

`docker run -d -p 80:80 --name nginx_container nginx`

```sh
C:\Windows\System32>docker run -d -p 80:80 --name nginx_container nginx
Unable to find image 'nginx:latest' locally
latest: Pulling from library/nginx
f11c1adaa26e: Pull complete
c6b156574604: Pull complete
ea5d7144c337: Pull complete
1bbcb9df2c93: Pull complete
537a6cfe3404: Pull complete
767bff2cc03e: Pull complete
adc73cb74f25: Pull complete
Digest: sha256:67682bda769fae1ccf5183192b8daf37b64cae99c6c3302650f6f8bf5f0f95df
Status: Downloaded newer image for nginx:latest
50e51e13a381e10df654c2c0ea616c12d5d9ab994942d3531aedcc65684b5662
```

## 4. Create Custom Image

Create a custom Docker image from the running container and name it my_website. Tag the container with the latest tag:

`docker commit nginx_container my_website:latest`

## 5. Remove Original Container

Remove the original container (nginx_container) and verify that it has been successfully removed:

`docker rm -f nginx_container`

## 6. Create New Container

Create a new container using the custom image you've created (the same way as the original container):

`docker run -d -p 80:80 --name my_website_container my_website:latest`

```sh
C:\Windows\System32>cd "C:\Users\tgakh\Documents"

C:\Users\tgakh\Documents>docker cp index.html nginx_container:/usr/share/nginx/html/index.html
Successfully copied 2.05kB to nginx_container:/usr/share/nginx/html/index.html

C:\Users\tgakh\Documents>docker commit nginx_container my_website:latest
sha256:e7fab5fac1eaade5c8fad5324277cfab4e6c0d50ff8a8a6dabf352cf3c021ccc

C:\Users\tgakh\Documents>docker rm -f nginx_container
nginx_container

C:\Users\tgakh\Documents>docker run -d -p 80:80 --name my_website_container my_website:latest
f3d41dec9d493a08d058ecd2bca1dc410df9ac0e78e1508a40485f07c30e94a3

C:\Users\tgakh\Documents>
```

## 7. Test Web Server

Access the web server at 127.0.0.1:80:

![Nginx Site](/media/nginxSite.png)

## 8. Analyze Image Changes

Use the docker diff command to analyze the changes made to the new image:

`docker diff my_website_container`

```sh
C:\Users\tgakh\Documents>docker diff my_website_container
C /run
C /run/nginx.pid
C /etc
C /etc/nginx
C /etc/nginx/conf.d
C /etc/nginx/conf.d/default.conf

C:\Users\tgakh\Documents>
```
