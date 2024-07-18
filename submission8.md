# Container Management

## List Containers Command and Output
```
CONTAINER ID   IMAGE                COMMAND                  CREATED             STATUS                       PORTS                                                                                                                                                 NAMES
a8118aabfe03   ipfs/go-ipfs         "/sbin/tini -- /usr/…"   About an hour ago   Up About an hour (healthy)   0.0.0.0:4001->4001/tcp, :::4001->4001/tcp, 0.0.0.0:5001->5001/tcp, :::5001->5001/tcp, 4001/udp, 0.0.0.0:8080->8080/tcp, :::8080->8080/tcp, 8081/tcp   ipfs_host
04f5c6be30ae   scenegenai_backend   "/opt/nvidia/nvidia_…"   3 weeks ago         Created                      0.0.0.0:8000->8000/tcp, :::8000->8000/tcp                                                                                                             backend
a7159d503290   hello-world          "/hello"                 3 weeks ago         Exited (0) 3 weeks ago                                                                                                                                                             determined_ptolemy
```

## Pull Latest Ubuntu Image Command
```
docker pull ubuntu:latest
```

## Run Container Command and Details
```
docker run -it --name ubuntu_container ubuntu:latest
```

## Remove Image Command and Outcome
```
docker rmi ubuntu:latest
Untagged: ubuntu:latest
Untagged: ubuntu@sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Deleted: sha256:35a88802559dd2077e584394471ddaa1a2c5bfd16893b829ea57619301eb3908
Deleted: sha256:a30a5965a4f7d9d5ff76a46eb8939f58e95be844de1ac4a4b452d5d31158fdea
```

# Image and Container Operations

## Create Image Archive Commands
```
docker pull ubuntu:latest
docker save -o ubuntu_image.tar ubuntu:latest
```

## Size Comparison
```
Original Image Size: 78.1MB
Archive File Size: 77M
```

### Explanation
The size difference may be due to compression in the archive process.
## Run Nginx Container Command and Verification
```
docker run -d -p 80:80 --name nginx_container nginx
curl http://127.0.0.1:80
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

## Create HTML File and Copy to Container
```
echo -e "<html>\n<head>\n<title>The best</title>\n</head>\n<body>\n<h1>website</h1>\n</body>\n</html>" > index.html
docker cp index.html nginx_container:/usr/share/nginx/html/index.html
```

## Create Custom Image Command
```
docker commit nginx_container my_website:latest
```

## Remove Original Container Command and Verification
```
docker rm -f nginx_container
Error response from daemon: No such container: nginx_container
```

## Create New Container Command
```
docker run -d -p 80:80 --name my_website_container my_website:latest
```

## Test Web Server Command and Output
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

## Analyze Image Changes Command and Output
```
docker diff my_website_container
C /etc
C /etc/nginx
C /etc/nginx/conf.d
C /etc/nginx/conf.d/default.conf
C /run
C /run/nginx.pid
```

### Explanation
The output of the `docker diff` command lists the changes made to the filesystem of the container. Lines prefixed with 'A' indicate added files, 'C' indicate changed files, and 'D' indicate deleted files. In this case, the output shows the changes made to the Nginx web server configuration and content files, such as the addition of our custom `index.html` file.
