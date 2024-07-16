# Task 1: Artifact Registries Research

## AWS Artifact Registries

**1. Amazon Elastic Container Registry (ECR)**
- **Description**: A fully managed Docker container registry that makes it easy to store, manage, and deploy Docker container images.
- **Key Features**:
  - Integration with Amazon ECS, EKS, and Lambda.
  - High availability and durability.
  - Image vulnerability scanning.
  - Lifecycle policies for automated image cleanup.

**2. AWS CodeArtifact**
- **Description**: A fully managed artifact repository service that makes it easy for organizations to securely store, publish, and share software packages used in their software development process.
- **Key Features**:
  - Support for multiple package formats (npm, PyPI, Maven, NuGet).
  - Integration with AWS CodeBuild, CodePipeline, and other CI/CD tools.
  - Fine-grained access control with AWS IAM.
  - Encryption at rest and in transit.

## GCP Artifact Registries

**1. Google Container Registry (GCR)**
- **Description**: A private Docker image storage system on Google Cloud Platform.
- **Key Features**:
  - Integration with Google Kubernetes Engine (GKE).
  - Vulnerability scanning.
  - Regional and multi-regional repositories.
  - IAM-based access control.

**2. Google Artifact Registry**
- **Description**: A single place for your organization to manage container images and language packages.
- **Key Features**:
  - Support for Docker, Maven, npm, and Python packages.
  - Integration with Google Cloud Build and other CI/CD tools.
  - Fine-grained access control with IAM.
  - Regional and multi-regional repositories.

## Azure Artifact Registries

**1. Azure Container Registry (ACR)**
- **Description**: A managed Docker container registry service used to store private Docker container images.
- **Key Features**:
  - Integration with Azure Kubernetes Service (AKS).
  - Geo-replication for high availability.
  - Content Trust for image signing.
  - Vulnerability scanning.

**2. Azure Artifacts**
- **Description**: A service that provides integrated package management for your CI/CD pipelines.
- **Key Features**:
  - Support for Maven, npm, NuGet, and Python packages.
  - Integration with Azure DevOps.
  - Universal Packages for storing any type of file.
  - Fine-grained access control.

# Task 2: Serverless Computing Platform Research

## AWS Serverless Computing Platforms

**1. AWS Lambda**
- **Description**: A serverless compute service that lets you run code without provisioning or managing servers.
- **Key Features**:
  - Automatic scaling.
  - Supports multiple programming languages (Node.js, Python, Java, Go, Ruby, etc.).
  - Integrated with other AWS services (S3, DynamoDB, Kinesis, etc.).
  - Pay only for the compute time you consume.

**2. AWS Fargate**
- **Description**: A serverless compute engine for containers that works with Amazon ECS and EKS.
- **Key Features**:
  - No need to manage servers or clusters.
  - Supports Docker containers.
  - Automatic scaling and load balancing.
  - Integrated with AWS services (CloudWatch, IAM, etc.).

## GCP Serverless Computing Platforms

**1. Google Cloud Functions**
- **Description**: A serverless execution environment for building and connecting cloud services.
- **Key Features**:
  - Event-driven functions.
  - Supports multiple programming languages (Node.js, Python, Go, Java, etc.).
  - Integrated with other GCP services (Pub/Sub, Firestore, etc.).
  - Pay only for the resources you use.

**2. Google Cloud Run**
- **Description**: A managed compute platform that automatically scales your stateless containers.
- **Key Features**:
  - Supports any containerized application.
  - Fully managed and scalable.
  - Integrated with other GCP services (Cloud Build, Stackdriver, etc.).
  - Pay only for the resources you use.

## Azure Serverless Computing Platforms

**1. Azure Functions**
- **Description**: A serverless compute service that enables you to run event-triggered code without having to explicitly provision or manage infrastructure.
- **Key Features**:
  - Event-driven functions.
  - Supports multiple programming languages (C#, JavaScript, Python, etc.).
  - Integrated with other Azure services (Cosmos DB, Event Grid, etc.).
  - Pay only for the compute resources you use.

**2. Azure Container Instances (ACI)**
- **Description**: A serverless container service that allows you to run containers without managing virtual machines.
- **Key Features**:
  - Supports Docker containers.
  - Quick and easy deployment.
  - Integrated with other Azure services (Azure Monitor, Azure Virtual Network, etc.).
  - Pay only for the resources you use.