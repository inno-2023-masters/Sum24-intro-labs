# Cloud Computing Lab - Artifact Registries and Serverless Computing Platforms

## Task 1: Artifact Registries Research

### AWS Artifact Registries
1. **Amazon Elastic Container Registry (ECR)**
   - **Description**: A fully managed Docker container registry that makes it easy to store, manage, and deploy Docker container images.
   - **Key Features**:
     - Integrated with Amazon ECS, EKS, and Lambda
     - High availability and durability
     - Image vulnerability scanning
     - Lifecycle policies for image management

2. **AWS CodeArtifact**
   - **Description**: A fully managed artifact repository service that makes it easy to store, publish, and share software packages used in your software development process.
   - **Key Features**:
     - Supports multiple package formats (npm, Maven, PyPI, etc.)
     - Integrated with AWS CodeBuild and AWS CodePipeline
     - Fine-grained access control with AWS IAM
     - Version tracking and dependency resolution

### GCP Artifact Registries
1. **Google Container Registry (GCR)**
   - **Description**: A single place for your team to manage Docker images, perform vulnerability analysis, and decide who can access what with fine-grained access control.
   - **Key Features**:
     - Integrated with Google Kubernetes Engine (GKE) and Cloud Run
     - Global availability and reliability
     - Vulnerability scanning
     - Granular access control with IAM

2. **Artifact Registry**
   - **Description**: Fully managed service that provides single place to manage your container images and language packages (npm, Maven, PyPI, etc.).
   - **Key Features**:
     - Unified repository for containers and packages
     - Integration with CI/CD pipelines
     - Fine-grained access control and encryption
     - Support for multiple artifact formats

### Azure Artifact Registries
1. **Azure Container Registry (ACR)**
   - **Description**: A managed, private Docker registry service based on the open-source Docker Registry 2.0.
   - **Key Features**:
     - Geo-replication for global distribution
     - Integrated with Azure Kubernetes Service (AKS) and Azure DevOps
     - Automated image builds and tasks
     - ACR Tasks for automated container image builds

2. **Azure Artifacts**
   - **Description**: A service for hosting and sharing packages with your team and managing package dependencies in your CI/CD pipelines.
   - **Key Features**:
     - Supports Maven, npm, NuGet, Python, and Universal Packages
     - Integration with Azure DevOps
     - Upstream sources to proxy and cache external packages
     - Detailed insights and reporting

## Task 2: Serverless Computing Platform Research

### AWS Serverless Computing Platforms
1. **AWS Lambda**
   - **Description**: A compute service that lets you run code without provisioning or managing servers.
   - **Key Features**:
     - Supports multiple languages (Node.js, Python, Java, Ruby, C#, Go, PowerShell)
     - Automatic scaling and pay-per-use pricing
     - Integration with many AWS services
     - Built-in monitoring and logging with Amazon CloudWatch

2. **AWS Fargate**
   - **Description**: A serverless compute engine for containers that works with Amazon ECS and EKS.
   - **Key Features**:
     - Removes the need to provision and manage servers
     - Seamless integration with ECS and EKS
     - Pay for vCPU and memory resources per application
     - Security isolation at the task level

### GCP Serverless Computing Platforms
1. **Google Cloud Functions**
   - **Description**: A lightweight, event-driven compute solution for developers to create single-purpose, stand-alone functions that respond to cloud events.
   - **Key Features**:
     - Supports Node.js, Python, Go, Java, .NET, and Ruby
     - Automatic scaling and pay-per-use pricing
     - Integration with Google Cloud services and third-party services
     - Built-in monitoring and logging with Google Cloud Monitoring

2. **Google Cloud Run**
   - **Description**: A managed compute platform that automatically scales your stateless containers.
   - **Key Features**:
     - Supports any programming language, runtime, or library
     - Can be triggered by HTTP requests or Pub/Sub events
     - Integrated with GCP's CI/CD tools
     - Pay-per-use pricing model

### Azure Serverless Computing Platforms
1. **Azure Functions**
   - **Description**: A serverless compute service that lets you run event-triggered code without having to explicitly provision or manage infrastructure.
   - **Key Features**:
     - Supports multiple languages (C#, Java, JavaScript, Python, PowerShell)
     - Built-in scaling and pay-per-execution pricing
     - Integration with Azure and third-party services
     - Advanced debugging and monitoring capabilities

2. **Azure Container Instances (ACI)**
   - **Description**: A service that allows you to run containers without managing servers.
   - **Key Features**:
     - Fast startup times and on-demand compute power
     - Supports Docker containers
     - Integration with Azure Kubernetes Service (AKS)
     - Per-second billing

