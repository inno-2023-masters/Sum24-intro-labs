# Task 2: Terraform Installation and Nginx Deployment

## 1. Research and Installation

Install Terraform on your system by following the official instructions.
Run this command:

```bash
wget https://releases.hashicorp.com/terraform/1.0.0/terraform_1.0.0_linux_amd64.zip
```

(Here was some problems to install terraform on Ubuntu because of region constraints)
So i decided to Install Terraform on Windows my secondary OS in dualboot configuration:
Download Terraform:

Terraform Configuration:

`main.tf:`

```
provider "docker" {
  host = "npipe:////.//pipe//docker_engine"
}

resource "docker_image" "nginx" {
  name = "nginx:latest"
  keep_locally = false
}

resource "docker_container" "nginx" {
  image = docker_image.nginx.latest
  name  = "tutorial"
  ports {
    internal = 80
    external = 8000
  }
}
```

`variables.tf:`

```
variable "nginx_image" {
default = "nginx:latest"
}

variable "container_name" {
default = "nginx-container"
}

variable "internal_port" {
default = 80
}

variable "external_port" {
default = 8080
}
```

## Commands Executed

```sh
$ touch main.tf
$ terraform init
$ terraform apply
```

Observations and Challenges

- During the installation, ensure that the PATH is correctly set.
- While deploying Nginx, make sure Docker is running.
