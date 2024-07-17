# Task 1: Artifact Registries in AWS, GCP, and Azure

## AWS

**1. Amazon Elastic Container Registry**

Stores, manages, and deploys Docker container images.

**Key features**:
  - Fully managed container registry.
  - Integrated with Amazon ECS, EKS, and AWS Lambda.
  - Supports Docker CLI and APIs.
  - Security: Encrypted images in transit and at rest, integration with IAM for access control.
  - Scalable: Designed to scale with your infrastructure.
  - Automated image scanning for vulnerabilities.
  - Cross-region replication for high availability.

**2. AWS CodeArtifact**

Securely stores and shares software packages used in the development process.

**Key features**:
  - Supports multiple package formats (npm, PyPI, Maven, and NuGet).
  - Integrated with AWS CodeBuild, AWS CodePipeline, and AWS CodeDeploy.
  - Automated dependency updates.
  - Security: Encrypted at rest and in transit, IAM integration for fine-grained access control.
  - Simplifies the sharing of packages within an organization and with external users.
  - Centralized repository for managing dependencies.

## GCP

**1. Google Container Registry**

Stores and manages Docker container images.

**Key Features**:
  - Fully managed Docker container registry.
  - Integrated with Google Kubernetes Engine (GKE) and other GCP services.
  - Supports regional and multi-regional repositories.
  - Security: Encrypted storage and vulnerability scanning.
  - IAM-based access control.
  - Easy to set up and use with the Docker CLI.
  - Access logs for audit purposes.

**2. Google Artifact Registry**

Universal repository manager for different artifact types.

**Key features**:
  - Supports Docker container images, npm packages, Maven artifacts, and more.
  - Integrated with GCP services like Google Kubernetes Engine (GKE) and Cloud Build.
  - Fine-grained access control using IAM.
  - Automated security vulnerability scanning.
  - High availability with multi-region support.
  - Unified platform for managing all types of artifacts.

## Azure

**1. Azure Container Registry**

Manages container images and related artifacts.

**Key features**:
  - Fully managed Docker container registry.
  - Integrated with Azure Kubernetes Service (AKS), Azure DevOps, and other Azure services.
  - Support for Helm charts, OCI artifacts, and Docker images.
  - Security: Built-in vulnerability scanning, content trust, and geo-replication.
  - Automated tasks for building, testing, and patching container images.
  - Scalable and highly available.

**2. Azure Artifacts**

Manages and shares packages for continuous integration and delivery.

**Key features**:
  - Supports multiple package types: NuGet, npm, Maven, Python, and Universal Packages.
  - Integrated with Azure DevOps Services.
  - Universal Packages support for storing binary files.
  - Security: Granular access control with Azure Active Directory.
  - Retention policies for automatic clean-up of old versions.
  - Easy consumption of packages from various sources.

# Task 2: The Best Serverless Computing Platforms in AWS, GCP, and Azure
## AWS

**1. AWS Lambda**

Runs code without provisioning or managing servers.

**Key features**:
  - Supports various programming languages (Node.js, Python, Java, Ruby, C#, Go, etc.).
  - Automatically scales based on the number of incoming requests.
  - Pay only for compute time (billed in milliseconds).
  - Integrated with other AWS services (S3, DynamoDB, API Gateway, etc.).
  - Built-in fault tolerance and high availability.
  - Environment variables support for configuration.
  - Monitoring and logging with AWS CloudWatch.
  - Secure by design with AWS IAM integration for permissions.

**2. AWS Fargate**

Runs containers without managing servers or clusters.

**Key features**:
  - Integrates with Amazon ECS and EKS.
  - Automatic scaling and load balancing.
  - Pay for vCPU and memory resources used by the containerized applications.
  - Secure with IAM roles for tasks.
  - Simplifies deployment by abstracting infrastructure management.

## GCP

**1. Google Cloud Functions**

Event-driven serverless compute platform for executing code in response to events.

**Key features**:
  - Supports Node.js, Python, Go, and Java.
  - Scales automatically based on the number of requests.
  - Integrated with GCP services like Cloud Pub/Sub, Cloud Storage, and Firebase.
  - Pay only for compute time (billed to the nearest 100 milliseconds).
  - Built-in logging and monitoring with Google Cloud Monitoring.
  - Secure execution environment with IAM roles.
  - Easily deployable via CLI, SDKs, and the console.

**2. Google Cloud Run**

Fully managed compute platform for running containerized applications.

**Key features**:
  - Automatically scales containers up or down based on traffic.
  - Supports any runtime or programming language.
  - Integrated with other GCP services.
  - Pay only for resources used while the container is active.
  - Secure with built-in IAM policies and VPC network support.
  - Deploy directly from source or Docker images.
  - Enables HTTP-triggered container execution.

## Azure

**1. Azure Functions**

Event-driven serverless compute platform for running small pieces of code.

**Key features**:
  - Supports multiple programming languages (C#, JavaScript, Python, Java, PowerShell, etc.).
  - Automatic scaling based on demand.
  - Pay-per-execution pricing model.
  - Integrated with Azure services like Azure Event Grid, Azure Cosmos DB, and Azure Service Bus.
  - Secure with Azure Active Directory and managed identities.
  - Built-in monitoring and diagnostics with Azure Monitor.
  - Local development and debugging support.
  - Durable Functions for long-running workflows and stateful functions.

**2. Azure Container Instances (ACI)**

Easily runs containers without managing virtual machines.

**Key Features**:
  - Supports Docker containers.
  - Instant provisioning of containers.
  - Integrated with Azure Kubernetes Service (AKS).
  - Pay per second for container usage.
  - Secure with virtual network integration and Azure AD.
  - Provides persistent storage options.
  - Ideal for burst workloads and data processing tasks.
