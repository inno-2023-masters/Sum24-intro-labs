# Containers Lab - Docker

## Task 2: Image and Container Operations

1. **Create Image Archive**:

```
igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ docker save -o ubuntu_image.tar ubuntu:latest

igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ ls -lh | grep ubuntu_image.tar
-rw------- 1 igor igor  77M июл  3 22:08 ubuntu_image.tar

igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ docker image ls | grep ubuntu
ubuntu           latest    35a88802559d   3 weeks ago   78.1MB
```

The sizes are the same.

2. **Run Nginx Container**:

```
igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ sudo systemctl stop apache2

igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ docker run -d -p 80:80 --name nginx_container nginx
4b303d24cc917f5ad80cad33aaa618bfd80a67f662bab6f9cf80aaceb59f14f5

igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ curl 127.0.0.1:80
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

3. **Create HTML File**:

```
igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ docker cp index.html nginx_container:/usr/share/nginx/html/index.html
Successfully copied 2.05kB to nginx_container:/usr/share/nginx/html/index.html

igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ curl 127.0.0.1:80
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
igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ docker commit nginx_container my_website:latest
sha256:20b60e60c7349c22bbad48500588acd1d80294d3098bb99bf50db39081e5bc8b
```

5. **Remove Original Container**:

```
igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ docker rm -f nginx_container
nginx_container

igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ docker ps -a | grep nginx_container
```

6. **Create New Container**:

```
igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ docker run -d -p 80:80 --name my_website_container my_website:latest
f7e4d2b6fbac7a4872f4b3ec47a6d7db0f1dfd70ea8479cd537bb362d9766ca4
```

7. **Test Web Server**:

```
igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ curl http://127.0.0.1:80
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
igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ docker diff my_website_container
C /etc
C /etc/nginx
C /etc/nginx/conf.d
C /etc/nginx/conf.d/default.conf
C /run
C /run/nginx.pid
```

The `diff` shows changes starting from the creation of the container. If we update the `index.html` file now, it will appear in `diff` output.
