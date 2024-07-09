# Lab 8 Containers Lab - Docker

## Image and Container Operations

1. **Create Image Archive:**
``docker save -o ubuntu_image.tar ubuntu:latest``

```
C:\Users\dimoninbirsk>docker images
REPOSITORY                        TAG       IMAGE ID       CREATED        SIZE
ubuntu                            latest    35a88802559d   4 weeks ago    78.1MB
goresumeapi                       dev       2d1fd27dfd79   5 weeks ago    212MB
testtesttest                      dev       5bb24fdd8343   5 weeks ago    212MB
mcr.microsoft.com/dotnet/aspnet   7.0       ec861be01768   5 weeks ago    212MB
sonarqube                         latest    ba3b520d50ea   4 months ago   797MB
```
![alt text](image.png)

__Size Comparation:__
Original image: 78.1MB
Archive file: 76.8MB

2. __Run NGINX container:__

As I do not pull NGINX container before, it automatically pull it and then run.

```
C:\Users\dimoninbirsk>docker run -d -p 80:80 --name nginx_container nginx
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
7e35b9c600b692beea0c51bd6d9b6e30b896a3cda89db8467f16ee629e9b6293
```

Now I can access __Welcome to nginx!__ page with ``localhost`` in browser.

![alt text](image-1.png)

3. __Create HTML File:__

After I created ``index.html`` file and move it inside docker container with ``docker cp index.html nginx_container:/usr/share/nginx/html/index.html`` I can see that web-page is changed.

![alt text](image-2.png)

4. __Create Custom Image__:

```
C:\Users\dimoninbirsk>docker commit nginx_container my_website:latest
sha256:31108844f50139900d2487ea8207ca1dcb5f7309d443f84c00bf2a0772ab882d
```

5. __Remove Original Container__

```
C:\Users\dimoninbirsk>docker rm -f nginx_container
nginx_container
```

6. __Create New Container__

```
C:\Users\dimoninbirsk>docker run -d -p 80:80 --name my_website_container my_website:latest
4629e86cf37d85238aaa7fd53078de787d8bfea36cb2d17d6f36f6fa3855426e
```

7. __Test Web Server__

```
C:\Users\dimoninbirsk>curl http://127.0.0.1:80
<html>
<head>
<title>The best</title>
</head>
<body>
<h1>website</h1>
</body>
</html>
```

8. __Analyze Image Changes__

The output of docker diff will show the changes made to the new image compared to its parent image. 

As we add ``index.html`` in Nginx server, it configured to send this file as responce instead of default page. 

```
C:\Users\dimoninbirsk>docker diff my_website_container
C /run
C /run/nginx.pid
C /etc
C /etc/nginx
C /etc/nginx/conf.d
C /etc/nginx/conf.d/default.conf
```


