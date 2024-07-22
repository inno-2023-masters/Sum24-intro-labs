# Submission for Lab 8

## Task 1

### Running `docker ps -a`

![ps](/Resources/ps.png)

### Pulling image of `ubuntu:latest`

![pull](/Resources/pull.png)

### Running image

![run](/Resources/run.png)

### Removing image

If we run the command with a container using it, we get the following error:
![rmi error](/Resources/rmi%20error.png)

Therefore, we first need to delete the container using it then we can remove the image:
![rmi](/Resources/rmi.png)

## Task 2

### Creating an archive file

![Archive](/Resources/archive.png)

From the size comparison, we can see that the image is almost the same size, only 0.5MB smaller. This might be due to some extra metadata required by the archive.

### Running an NGINX container

![Run nginx](/Resources/run%20nginx.png)
![nginx running](/Resources/nginx%20running.png)

### Copying new index into container

![cp](/Resources/cp.png)

### Committing the changes and creating a new container

![commit](/Resources/commit.png)

### Running curl on the new container

![curl](/Resources/curl.png)

### Running diff on the new container

![diff](/Resources/diff.png)

The files shown from the `diff` command are the files that have been changed from the original image. Seeing the files, they seem like internal nginx files that change during runtime.
