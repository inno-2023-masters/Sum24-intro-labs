
# Task 1: Container Management

## List Containers

Command:
```bash
docker ps -a
```

Output:
```
CONTAINER ID   IMAGE         COMMAND       CREATED          STATUS                      PORTS     NAMES
```

*(Note: I don't have running containers now.)*

## Pull Latest Ubuntu Image

Command:
```bash
docker pull ubuntu:latest
```

Output:
```
latest: Pulling from library/ubuntu
Digest: sha256:xxxxxx
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest
```

## Run Container

Command:
```bash
docker run -it --name ubuntu_container ubuntu:latest
```

Details:
- The container will run interactively (`-it`).
- The container is named `ubuntu_container`.
- It uses the `ubuntu:latest` image.

## Remove Image

Command:
```bash
docker rmi ubuntu:latest
```

Outcome:
- If the image is being used by any container (running or stopped), you will see an error message similar to:
  ```
  Error response from daemon: conflict: unable to delete 26b77e58432b (cannot be forced) - image is being used by running container abc123
  ```
- If no containers are using the image, it will be removed successfully:
  ```
  Untagged: ubuntu:latest
  Deleted: sha256:xxxxxx
  ```


# Docker Image and Container Operations

## Create Image Archive

### Pull the Latest Ubuntu Image

Command:
```bash
docker pull ubuntu:latest
```

### Create an Archive File

Command:
```bash
docker save -o ubuntu_image.tar ubuntu:latest
```

### Compare the Size of the Archive File

The size of the archive file and the original image might differ due to compression applied during the save operation. The `docker save` command includes only the actual image data, whereas the Docker image may include additional metadata.

## Run Nginx Container

### Run the Nginx Container

Command:
```bash
docker run -d -p 80:80 --name nginx_container nginx
```

### Verify the Web Server

You can verify the web server is running and accessible by visiting `http://127.0.0.1` in your web browser.

## Create HTML File

### Create the HTML File

Content:
```html
<html>
<head>
<title>The best</title>
</head>
<body>
<h1>website</h1>
</body>
</html>
```

### Copy the HTML File to the Container

Command:
```bash
docker cp index.html nginx_container:/usr/share/nginx/html/index.html
```

## Create Custom Image

### Create a Custom Docker Image

Command:
```bash
docker commit nginx_container my_website:latest
```

## Remove Original Container

### Remove the Original Container

Command:
```bash
docker rm -f nginx_container
```

## Create New Container

### Create a New Container from the Custom Image

Command:
```bash
docker run -d -p 80:80 --name website_container website:latest
```

## Test Web Server

### Use curl to Access the Web Server

Command:
```bash
curl http://127.0.0.1:80
```

## Analyze Image Changes

### Use docker diff to Analyze Changes

Command:
```bash
docker diff website_container
```

### Explain the Output of docker diff

The `docker diff` command shows the changes made to the filesystem of the container. It lists files and directories that have been added, deleted, or modified. The output can be interpreted as:
- `A` indicates a file or directory that has been added.
- `D` indicates a file or directory that has been deleted.
- `C` indicates a file or directory that has been changed.
