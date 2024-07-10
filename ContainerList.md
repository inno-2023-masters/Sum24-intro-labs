# Task 1: Container Management

## 1. List containers using "ps -a" command

![ps](images/ps.png)

## 2. Pull Latest Ubuntu Image using "docker pull ubuntu:latest" command

![pull](images/pull.png)

Check the installed image using "docker images" command

![images1](images/images1.png)

## 3. Run Container using "docker run -it --name ubuntu_container ubuntu:latest" command

![run](images/run.png)

Check the active container using "ps -a" command

![ps1](images/ps1.png)

## 4. Remove the Ubuntu image using "docker rmi ubuntu:latest"

![rmi](images/rmi.png)

Check that the image was removed using "docker images" command

![images](images/images.png)

# Task 2: Image and Container Operations

## 1. Create Image Archive using "docker save -o ubuntu_image.tar ubuntu:latest" command

Compare the package size using "ls -lh | grep ubuntu" command

Created image's size:

![image_tar](images/image_tar.png)

Initial pulled image's size:

![images1](images/images1.png)

**Result: the size of manually created image is 1.1M less than the initial size of the pulled image.**

## 2. Run Nginx Container using "docker run -d -p 80:80 --name nginx_container nginx"

![run_nginx](images/run_nginx.png)

Verify that the container is up and the server accessible via the browser

![ps2](images/ps2.png)

![web](images/web.png)

## 3. Create HTML File

![cat_index](images/cat_index.png)

 Copy the HTML file to the container using "docker cp index.html nginx_container:/usr/share/nginx/html/index.html"

 ![copy_index](images/copy_index.png)

 ## 4. Create Custom Image with name "my_website" and tag "latest" using "docker commit nginx_container my_website:latest" command

 ![commit](images/commit.png)

 Check the created image

 ![images2](images/images2.png)

 ## 5. Remove Original nginx_container using "docker rm -f nginx_container" command

 ![rm_container](images/rm_container.png)

 Check that the container was removed

  ![ps](images/ps.png)

 ## 6. Create new container using the image my_website "docker run -d -p 80:80 --name my_website_container my_website:latest"

![run_my_website](images/run_my_website.png)

 ## 7. Test Web Server via terminal using "curl http://127.0.0.1:80"

![curl](images/curl.png)

 ## 8. Analyze Image Changes using "docker diff my_website_container" command

![diff](images/diff.png)

The changes of the configuration file relate to the added index.html file while the changes of nginx.pid relate to the container's restarts.
