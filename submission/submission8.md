# Lab 8

## Task 1

1. To see all containers, use the command `docker ps -a`.
   ![alt text](1.png)

2. Pull an image from Docker Hub.
   ![alt text](2.png)

3. Start a new Ubuntu container with `docker run -it --name ubuntu_container ubuntu:latest`.
   ![alt text](3.0.png)

4. Attempt to delete the image.
   ![alt text](3.png)

## Task 2

1. Create an archive of the Ubuntu image.
   ![alt text](4.png) ![alt text](6.png)

2. Launch an Nginx container with a custom index page.
    - `docker run -d -p 80:80 --name nginx_container nginx`
    - ![alt text](7.png)
    - ![alt text](8.png)
    - ![alt text](9.png)
    - ![alt text](10.png)

3. Save the current state of the Nginx container with `docker commit nginx_container my_website:latest`.
    - ![alt text](11.png)

4. Stop and remove the current Nginx container:
    - `docker stop nginx_container && docker rm nginx_container`
    - ![alt text](12.png)

5. Run the saved container image and test it with `curl`.
    - `docker run -d -p 80:80 --name my_website_container my_website:latest`
    - `curl localhost`
    - ![alt text](13.png)
    - ![alt text](14.png)

6. Use `docker diff` to view file changes from the base image in the container.
   ![alt text](15.png)
    - `docker diff` displays modifications made to files since the original image build.
