# Terraform and Nginx Deployment

## Terraform Version
Terraform v1.4.6

## Installation Steps
1. **Ensure System is Up to Date and Required Packages are Installed**:
    - Ran the following command to update the system and install required packages:
      ```
      sudo apt-get update && sudo apt-get install -y gnupg software-properties-common curl
      ```

2. **Install Terraform Using Snap**:
    - Used the following command to install Terraform via snap:
      ```
      sudo snap install terraform --classic
      ```

3. **Verified Installation**:
    - Checked the installed version to verify the installation:
      ```
      terraform -version
      ```

## Commands Executed
1. **Initialized Terraform**:
    - Created and configured the `main.tf` file with the following content:
      ```
      terraform {
        required_providers {
          docker = {
            source  = "kreuzwerker/docker"
            version = "~> 3.0.1"
          }
        }
      }
 
      provider "docker" {
      }
 
      resource "docker_image" "nginx" {
       name = "nginx"
       keep_locally = false
       }
      resource "docker_container" "nginx" {
        image = docker_image.nginx.image_id
        name  = "tutorial"

        ports {
          internal = 80
          external = 80
        }
      }
      ```
    - Ran the following command to initialize Terraform:
      ```
      terraform init
      ```

2. **Applied the Terraform Configuration**:
    - Applied the configuration to create the infrastructure:
      ```
      terraform apply
      ```
    - Confirmed the apply step by typing `yes` when prompted.

3. **Verified Nginx Deployment**:
    - After Terraform applied the configuration, verified the Nginx container running:
      ```
      docker ps
      ```

4. **Destroyed the Infrastructure**:
    - To clean up and destroy the created infrastructure:
      ```
      terraform destroy
      ```
    - Confirmed the destroy step by typing `yes` when prompted.

## Observations and Challenges
- **VPN Requirement**: Encountered an issue where Terraform could not be initialized without using a VPN. The provider configuration and download of necessary plugins failed due to network restrictions. Using a VPN resolved this issue and allowed Terraform to initialize successfully.
- **Docker Integration with WSL**: Verified that Docker Desktop was running and WSL integration was enabled for the Ubuntu distribution.
- **Internet Connectivity**: Ensured WSL environment had internet access to reach the Terraform provider registry.
