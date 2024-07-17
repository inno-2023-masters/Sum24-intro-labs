## Task 1: Container Management

**Objective**: Manage Docker containers and images.

1. **List Containers**:

```
docker ps -a
CONTAINER ID   IMAGE               COMMAND                  CREATED          STATUS          PORTS     NAMES
9c59b25d4a95   map_loader:latest   "/ros_entrypoint.sh …"   18 seconds ago   Up 17 seconds             charming_euler
```

With ps command (and -a flag for more info) we can see which containers are running at a time. For my case I'm running a single example container for my work purposes. 

2. **Pull Latest Ubuntu Image**:

```
docker pull ubuntu:latest
latest: Pulling from library/ubuntu
9c704ecd0c69: Pull complete 
Digest: sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest
```
Here we are pulling an image for latest ubuntu version from docker hub.

3. **Run Container**:

```
docker run -it --name ubuntu_container ubuntu:latest
root@5262922679fd:/# 
```
Here we run this container using latest ubuntu image using interactive terminal session. By default we are in root mode, no other users are available. 

4. **Remove Image**:

First, we wil need to exit this container, so inside of the interactive shell we will write exit.
Second, we perform this command:

Before removal of an image let's use stop and remove container which is attached to ubuntu image:
```
docker stop ubuntu_container
ubuntu_container

docker container rm ubuntu_container 
ubuntu_container
```

When our image is not used anywhere, we can safely remove it.
```
docker rmi ubuntu:latest
Untagged: ubuntu:latest
Untagged: ubuntu@sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Deleted: sha256:35a88802559dd2077e584394471ddaa1a2c5bfd16893b829ea57619301eb3908
Deleted: sha256:a30a5965a4f7d9d5ff76a46eb8939f58e95be844de1ac4a4b452d5d31158fdea
```

If we would try to remove the image while still using container we would get:
```
docker rmi ubuntu:latest
Error response from daemon: conflict: unable to remove repository reference "ubuntu:latest" (must force) - container 5262922679fd is using its referenced image 35a88802559d
```

## Task 2: Image and Container Operations

1. **Create Image Archive**:

Let's download the image once again and try to create an archive tar from it:
```
docker save -o ubuntu_image.tar ubuntu:latest
```

We successfully downloaded it - let's compare sizes:

```
docker image ls
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
map_loader   latest    11b8e0756a05   2 hours ago   4.93GB
ubuntu       latest    35a88802559d   5 weeks ago   78.1MB
```

```
du -h ubuntu_image.tar 
77M	ubuntu_image.tar
```

The size of the tar file is a little bit smaller (< 1 MB) then the image in the docker storage system. That's probably because of Dockers internal layers structure + metadata files. 

2. **Run Nginx Container**:


Let's use the appropriate command to run a container using the Nginx web server image:

```
docker run -d -p 80:80 --name nginx_container nginx
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
926b5c9be2bcbb068feb4fb2975ae0b3ee383a9bdb983c75f2822c53fccf0ead
```

We successfully ran a ngninx container. Let's verify that:

```
docker ps -f name=nginx_container
CONTAINER ID   IMAGE     COMMAND                  CREATED              STATUS              PORTS                               NAMES
926b5c9be2bc   nginx     "/docker-entrypoint.…"   About a minute ago   Up About a minute   0.0.0.0:80->80/tcp, :::80->80/tcp   nginx_container

```

And let's also check it's accessibility with curl:

```
curl http://localhost
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

Indeed, message is correct.

3. **Create HTML File**:

1. I created and copied info to index.html file store in local folder.

2. I copied my file from my main system to docker container using cp:

```
docker cp index.html nginx_container:/usr/share/nginx/html/index.html
Successfully copied 2.05kB to nginx_container:/usr/share/nginx/html/index.html
```
Indeed, the content is displayed correctly:

```
curl http://localhost
<html>
<head>
<title>The best</title>
</head>
<body>
<h1>website</h1>
</body>
</html>
```

4. **Create Custom Image**:
```
    docker commit nginx_container my_website:latest
sha256:1a109a1872e981f0247878bf9b42d6cb5b627499af408a8f865c9e38b2092e60 
```

```
docker image ls
REPOSITORY   TAG       IMAGE ID       CREATED          SIZE
my_website   latest    1a109a1872e9   37 seconds ago   188MB
map_loader   latest    11b8e0756a05   2 hours ago      4.93GB
nginx        latest    fffffc90d343   3 weeks ago      188MB
ubuntu       latest    35a88802559d   5 weeks ago      78.1MB
```

5. **Remove Original Container**:
```
docker rm -f nginx_container
nginx_container
```

```
docker image ls
REPOSITORY   TAG       IMAGE ID       CREATED              SIZE
my_website   latest    1a109a1872e9   About a minute ago   188MB
map_loader   latest    11b8e0756a05   2 hours ago          4.93GB
nginx        latest    fffffc90d343   3 weeks ago          188MB
ubuntu       latest    35a88802559d   5 weeks ago          78.1MB

```

6. **Create New Container**:
```
docker run -d -p 80:80 --name my_website_container my_website:latest
caad8f654e5368a927fab255fee5d371438574d47b9256249974fa333446b5ac
```
7. **Test Web Server**:
```
curl http://127.0.0.1:80
<html>
<head>
<title>The best</title>
</head>
<body>
<h1>website</h1>
</body>
</html>
```

8. **Analyze Image Changes**:

```
 docker diff my_website_container
C /run
C /run/nginx.pid
C /etc
C /etc/nginx
C /etc/nginx/conf.d
C /etc/nginx/conf.d/default.conf
```

We can see three letters here, either C, A or D for create, add, delete. We see 6 Cs implying 6 changes in 3 directories. Here we can see that changed files are /etc/nginx/conf.d/default.conf and /run/nginx.pid. They are changed because nginx accessed and reloaded it's configuration on container creation. Also nginx.pid stores a process ID of the nginx server, id was initialized with container start. 