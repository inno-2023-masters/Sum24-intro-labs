# Lab 10 - Artifact Registries and Serverless Computing Platforms

## Task 1: Artifact Registries

Artifact registries are managed services that store and organize various packages, libraries, and container images for easier deployment and dependency management. AWS, GCP, and Azure each offer artifact registry solutions with similar core functions, though they differ in package support and integration specifics. Below is a summary of the main artifact registries and supported package types across these providers.

### Artifact Registries by Cloud Provider

1. **AWS - CodeArtifact**  
   [AWS CodeArtifact](https://docs.aws.amazon.com/codeartifact/latest/ug/welcome.html) is a fully managed artifact repository that supports a variety of package types:
    - Cargo
    - npm
    - Maven
    - NuGet
    - Python
    - Swift
    - Ruby
    - Generic files

2. **GCP - Artifact Registry**  
   [Google Artifact Registry](https://cloud.google.com/artifact-registry/docs/overview) consolidates multiple package types and container images in a single location:
    - Docker images
    - Maven
    - npm
    - Python
    - Helm charts
    - Go modules
    - Apt (Debian packages)
    - RPM packages
    - Generic files

3. **Azure - Artifacts**  
   [Azure Artifacts](https://learn.microsoft.com/en-us/azure/devops/artifacts/?view=azure-devops) provides a scalable, flexible repository for various package types, supporting:
    - Maven
    - npm
    - NuGet
    - Python
    - Gradle
    - Cargo
    - dotnet
    - Generic files

## Task 2: Serverless Computing Platforms

Serverless computing platforms allow developers to run backend functions and workflows without managing infrastructure. AWS, GCP, and Azure each offer robust serverless tools designed to handle diverse workloads and event-driven applications. Below are the primary serverless services available on each platform.

### Serverless Platforms by Cloud Provider

1. **AWS**  
   [AWS Serverless Services](https://aws.amazon.com/serverless/getting-started/) include tools for building and scaling applications without managing servers:
    - **AWS Lambda**: Runs event-triggered code for functions in multiple languages.
    - **Amazon API Gateway**: Configures and manages APIs.
    - **Amazon EventBridge**: Connects and routes events between AWS services and applications.
    - **AWS Fargate**: Serverless compute for containers using ECS and EKS.
    - **AWS Step Functions**: Orchestrates serverless workflows.
    - **Amazon Simple Notification Service (SNS)**: Sends notifications to users.
    - **Amazon Simple Queue Service (SQS)**: Manages message queues for application scaling.
    - **AWS Serverless Application Model (SAM)**: Framework for building and deploying serverless applications.

2. **GCP**  
   [Google Cloud Serverless Solutions](https://cloud.google.com/serverless) offer flexible, managed compute and workflow services:
    - **Google Cloud Functions**: Runs serverless functions in response to events; supports multiple languages.
    - **Google Cloud Run**: Deploys and auto-scales containerized applications based on HTTP requests or events.
    - **Google App Engine**: A platform-as-a-service (PaaS) for deploying web applications and backends.

3. **Azure**  
   [Azure Serverless Services](https://learn.microsoft.com/en-us/azure/logic-apps/logic-apps-serverless-overview) provide comprehensive tools for developing, deploying, and managing serverless workflows:
    - **Azure Functions**: Executes code in response to events; supports several languages.
    - **Azure Logic Apps**: Configures serverless workflows, connecting Azure services and APIs.
    - **Azure Container Instances (ACI)**: Runs containerized applications without orchestration, suitable for isolated workloads.

This document provides a concise comparison of artifact registries and serverless computing services across AWS, GCP, and Azure, highlighting the key features and supported tools available in each cloud platform.
