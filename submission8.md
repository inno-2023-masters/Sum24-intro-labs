# Containers Lab - Docker

## Task 1: Container Management

1. List Containers:  
    Command: `docker ps -a`
   ![Output of docker ps -a](./assets/docker-ps.png)
2. Pull Latest Ubuntu Image:  
    Command: `docker pull ubuntu:latest`
   ![Output of docker pull ubuntu:latest](./assets/docker-pull-ubuntu.png)
3. Run Container:
   Command: `docker run -it --name ubuntu_container ubuntu:latest`
   ![Output of docker run -it --name ubuntu_container ubuntu:latest](./assets/docker-run-ubuntu.png)
4. Remove Image:
   Command: `docker rmi ubuntu:latest`
   ![Output of docker rmi ubuntu:latest](./assets/docker-rmi-ubuntu.png)
