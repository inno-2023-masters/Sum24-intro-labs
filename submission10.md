# Lab 10 submission

## Task 1

### AWS Artifact Registries

1. **Amazon Elastic Container Registry (ECR)**
   - **Description**: A fully managed Docker container registry that makes it easy to store, manage, and deploy Docker container images.
   - **Key Features**:
     - Integrated with Amazon ECS, EKS, and Lambda
     - High availability and durability
     - Encryption at rest and in transit
     - Vulnerability scanning
     - Lifecycle policies

2. **AWS CodeArtifact**
   - **Description**: A fully managed artifact repository service that makes it easy to securely store, publish, and share software packages used in your software development process.
   - **Key Features**:
     - Supports Maven, Gradle, npm, yarn, and pip
     - Fine-grained access control
     - Integrated with AWS CodeBuild and CodePipeline
     - Version control and dependency management

### GCP Artifact Registries

1. **Google Artifact Registry**
   - **Description**: A universal repository manager for container images and non-container artifacts, such as Maven and npm packages.
   - **Key Features**:
     - Support for Docker images, Maven, npm, and Python packages
     - Integrated with Google Kubernetes Engine (GKE) and Cloud Run
     - IAM-based access control
     - Vulnerability scanning for container images
     - Regional and multi-regional support

### Azure Artifact Registries

1. **Azure Container Registry (ACR)**
   - **Description**: A managed Docker container registry service used for storing and managing container images.
   - **Key Features**:
     - Geo-replication for high availability
     - Integrated with Azure Kubernetes Service (AKS) and Azure DevOps
     - Content Trust for image signing
     - Automated image builds and tasks
     - Vulnerability scanning

2. **Azure Artifacts**
   - **Description**: A service for hosting and sharing packages (Maven, npm, NuGet, and Python) and integrating with CI/CD pipelines.
   - **Key Features**:
     - Universal package repository
     - Integration with Azure DevOps
     - Fine-grained access control
     - Upstream sources for external packages
     - Retention policies

## Task 2

### AWS Serverless Computing Platforms

1. **AWS Lambda**
   - **Description**: A compute service that lets you run code without provisioning or managing servers.
   - **Key Features**:
     - Supports multiple languages (Python, Node.js, Java, Go, etc.)
     - Automatic scaling and high availability
     - Integrated with other AWS services (S3, DynamoDB, Kinesis, etc.)
     - Pay-per-use pricing model
     - Event-driven architecture

2. **AWS Fargate**
   - **Description**: A serverless compute engine for containers that works with both Amazon ECS and Amazon EKS.
   - **Key Features**:
     - No need to manage servers or clusters
     - Automatically scales with your needs
     - Seamless integration with ECS and EKS
     - Supports Docker containers
     - Pay for vCPU and memory resources used

### GCP Serverless Computing Platforms

1. **Google Cloud Functions**
   - **Description**: A lightweight, event-driven compute solution for easily running small code snippets in the cloud.
   - **Key Features**:
     - Supports multiple languages (Node.js, Python, Go, etc.)
     - Automatic scaling and high availability
     - Integrated with other GCP services (Pub/Sub, Cloud Storage, etc.)
     - Pay-per-use pricing model
     - Event-driven architecture

2. **Google Cloud Run**
   - **Description**: A fully managed compute platform that automatically scales your stateless containers.
   - **Key Features**:
     - Supports any containerized application
     - Fully managed or Anthos-managed options
     - Automatic scaling from zero to n
     - Integrated with GCP services (Firestore, Pub/Sub, etc.)
     - Pay for what you use

### Azure Serverless Computing Platforms

1. **Azure Functions**
   - **Description**: An event-driven, serverless compute service that enables code execution without managing infrastructure.
   - **Key Features**:
     - Supports multiple languages (C#, Java, JavaScript, Python, etc.)
     - Automatic scaling and high availability
     - Integrated with other Azure services (Cosmos DB, Event Hubs, etc.)
     - Pay-per-use pricing model
     - Durable functions for stateful workflows

2. **Azure Container Instances (ACI)**
   - **Description**: A service that allows you to run Docker containers without managing virtual machines.
   - **Key Features**:
     - Quick and easy deployment of containers
     - Integrated with Azure Kubernetes Service (AKS)
     - Supports Docker images from ACR, Docker Hub, or other registries
     - Per-second billing for resources used
     - Virtual network support
