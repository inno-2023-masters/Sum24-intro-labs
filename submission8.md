# Docker
## Task 1 Configuration Management

1. **List Containers**:

    ```sh
     docker ps -a
     ```
    **Output**

    ![](.\images\listContainers.png)

2. **Pull Latest Ubuntu Image**:
     ```sh
     docker pull ubuntu:latest 
   ```
   **Output**

   ![](.\images\pullUbuntu.png)

3. **Run Container**:
  ```sh
  docker run -it --name ubuntu_container ubuntu:latest
  ```
   **Output**

   ![](.\images\runContainer.png)

4. **Remove Image**:
     ```sh
     docker rmi ubuntu:latest
     ```
   **Output**

   ![](.\images\removeContainer.png)

## Task 2: Image and Container Operations

1. **Create Image Archive**:

  ```sh
     docker save -o ubuntu_image.tar ubuntu:latest
   ```
**Output**

![](.\images\containerSize.png)

2. **Run Nginx Container**:
     ```sh
     docker run -d -p 8081:80 --name nginx_container nginx
     ```
   
   **Output**
- Test connection with telnet to port 8081
- 
![](.\images\telnetCommand.png)
- Result: Success

![](.\images\telneResult.png)

4. **Create Custom Image**:
```sh
     docker commit nginx_container my_website:latest
   ```
**Output**

![](.\images\createNewContainer.png)

5. **Remove Original Container**:

     ```sh
     docker rm -f nginx_container
     ```
   **Output**
Confirm Removal
![](.\images\confirmNgnRemoved.png)

6. **Create New Container**:
     ```sh
     docker run -d -p 8085:80 --name my_website_container my_website:latest
     ```

7. **Test Web Server**:
     ```sh
     curl http://127.0.0.1:8085
     ```
   Curl to website
   ![](.\images\curlTest.png)

8. **Analyze Image Changes**:
     ```sh
     docker diff my_website_container
     ```
   ![](.\images\diff.png)

This command shows all the files that were modified, which means the files displayed in the screenshot
are the modified ones.
