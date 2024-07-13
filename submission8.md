# Lab 8 submission

## Task 1

### List containers

![ps_a](screens/list_containers.png)

### Pull latest Ubuntu image

![ubuntu_latest](screens/ubuntu_latest.png)

### Run an Ubuntu container

![run](screens/run.png)

> We notice that by running the container with the `-it` argument, we connect to a bash shell inside the container. We did not specify the command for the container, which suggests that the container entrypoint is `/bin/bash` .

### Attempting to remove the Ubuntu image

![image-20240713172658836](screens/rm.png)

> We cannot remove the image because the container that we just created is referencing it.



## Task 2

### Saving the Ubuntu image to a file

After using the command `docker save -o ubuntu_image.tar ubuntu:latest` to save the image to a .tar file. We compare the size of the file to the size of the image:

![image-20240713173109150](screens/image.png)

![image-20240713173144640](screens/file.png)

We can see that the file is almost the same size as the image itself. This is because the `docker save` command saves the image to a tarball, which is uncompressed.

### Running an nginx container

> I had to first stop a default Apache server that was using port 80 using `sudo systemctl stop apache2.service`.

![image-20240713173803387](/home/rafik/Documents/InnoUni/sum24/Sum24-intro-labs-devops/screens/nginx.png)

The website is accessible once the container is up and running:

![image-20240713173936334](screens/locahost.png)

### Set up the website homepage

![image-20240713174341713](screens/website.png)



### Commit container

![image-20240713174759391](screens/commit.png)

### Remove old container and run a new container from the saved image

![image-20240713174937372](screens/rm_run.png)

### Accessing the website

![image-20240713175053413](screens/curl.png)

### Docker diff

![image-20240713175224434](screens/diff.png)

> We notice that 2 files are changed in the container, compared to the image. The files are shown in the screenshot and their parent directories are also marked as changed. Some automatic changes happened to the default.conf file, and the nginx.pid file was updated because nginx got a new PID when we started the container.

