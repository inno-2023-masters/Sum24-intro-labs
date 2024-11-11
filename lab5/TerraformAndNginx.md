# Terraform

1. Create "main.tf"
    ```tf
    terraform {
        required_providers {
            docker = {
            source = "kreuzwerker/docker"
            version = "~> 3.0.1"
            }
        }
        }

        provider "docker" {}

        resource "docker_image" "nginx" {
        name         = "nginx:latest"
        keep_locally = false
        }

        resource "docker_container" "nginx" {
        image = docker_image.nginx.image_id
        name  = "tutorial"
        ports {
            internal = 80
            external = 8000
        }
    }
    ```

2. `terraform init` ![alt text](1.png)


3. `terraform apply` ![alt text](2.png)![alt text](3.png)


4. `terraform destroy`![alt text](4.png)

- terraform version: v1.9.8
