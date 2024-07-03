# Containers Lab - Docker

## Task 1: Container Management

1. **List Containers**:

```
igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ docker ps -a
CONTAINER ID   IMAGE            COMMAND                  CREATED       STATUS                     PORTS     NAMES
967a6be218cc   lbs-server-lbs   "poetry run flask --…"   3 hours ago   Exited (137) 3 hours ago             lbs-server-lbs-1
e4417eec0f50   postgres:15.7    "docker-entrypoint.s…"   3 hours ago   Exited (0) 3 hours ago               lbs-server-db-1
```

2. **Pull Latest Ubuntu Image**:
```
igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ docker pull ubuntu:latest
latest: Pulling from library/ubuntu
9c704ecd0c69: Pull complete 
Digest: sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest
```

3. **Run Container**:
```
igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ docker run -it --name ubuntu_container ubuntu:latest

root@32b91d09954a:/# lsb_release -a
bash: lsb_release: command not found

root@32b91d09954a:/# cat /etc/os-release
PRETTY_NAME="Ubuntu 24.04 LTS"
NAME="Ubuntu"
VERSION_ID="24.04"
VERSION="24.04 LTS (Noble Numbat)"
VERSION_CODENAME=noble
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=noble
LOGO=ubuntu-logo
```

4. **Remove Image**:

```
igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ docker rmi ubuntu:latest
Error response from daemon: conflict: unable to remove repository reference "ubuntu:latest" (must force) - container 32b91d09954a is using its referenced image 35a88802559d

igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ docker rm 32b91d09954a
32b91d09954a

igor@igor-HP-Pavilion-Gaming-Laptop-15-ec1xxx:~/Sum24-intro-labs$ docker rmi ubuntu:latest
Untagged: ubuntu:latest
Untagged: ubuntu@sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Deleted: sha256:35a88802559dd2077e584394471ddaa1a2c5bfd16893b829ea57619301eb3908
Deleted: sha256:a30a5965a4f7d9d5ff76a46eb8939f58e95be844de1ac4a4b452d5d31158fdea
```