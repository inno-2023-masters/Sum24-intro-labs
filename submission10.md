# Lab 10

## Task 1

### 1. Amazon Web Services (AWS)

    Amazon Elastic Container Registry (ECR)

**Key features**:
- Fully managed Docker container registry.
- Integrated with Amazon ECS, EKS, and AWS Lambda.
- Supports OCI (Open Container Initiative) images.
- Provides high availability and durability with replication.
- Scalable and secure with AWS Identity and Access Management (IAM).
- Supports image vulnerability scanning.
- Lifecycle policies to manage image retention.
- Integrated with AWS CloudTrail for audit logging.

    **Artifact registry**: AWS CodeArtifact

**Key Features**:

- Managed artifact repository service.
- Supports popular package managers such as Maven, npm, Python (PyPI), and NuGet.
- Integrated with AWS CodeBuild, CodePipeline, and CodeDeploy.
- Provides fine-grained access control with IAM.
- Pay-as-you-go pricing model.
- Supports package versioning and dependency resolution.
- Encryption at rest and in transit.

### 2. Google Cloud Platform (GCP)

    Google Container Registry (GCR)

**Key Features**:
- Managed Docker container registry.
- Integrated with GKE and Google Cloud Build.
- Supports automated image vulnerability scanning.
- Global and regional repositories for low latency.
- Integrated with Cloud Identity and Access Management (IAM).
- Provides detailed audit logs through Cloud Audit Logs.
- Easy image tagging and version management.

    **Artifact registry**: Google Atrifact Registry

**Key features**:
- Unified repository for managing container images and language-specific packages.
- Supports Docker, Maven, npm, and Python (PyPI) packages.
- Integrated with Google Kubernetes Engine (GKE) and Cloud Build.
- Provides vulnerability scanning and insights.
- Granular access control using IAM.
- High availability and low latency through global and regional configurations.
- Automated build and deploy workflows.
- Policy enforcement and audit logging.

### 3. Microsoft Azure

    Azure Container Registry (ACR)

**Key Features**:
- Managed Docker container registry.
- Supports OCI images and Helm charts.
- Integrated with Azure Kubernetes Service (AKS) and Azure DevOps.
- Provides image build capabilities with ACR Tasks.
- Advanced security features with content trust and geo-replication.
- Vulnerability scanning via Microsoft Defender for Cloud.
- Supports private link and virtual network integrations.
- Role-based access control (RBAC) and Azure Active Directory (AAD) integration.

    **Artifact registry**: Azure Atrifact

**Key Features**:
- Managed artifact repository service within Azure DevOps.
- Supports Maven, npm, NuGet, and Python (PyPI) packages.
- Integrated with Azure DevOps CI/CD pipelines.
- Provides universal package repository.
- Pay-as-you-go pricing with scalable storage.
- Fine-grained access control and permissions.
- Supports upstream sources and caching.


## Task 2

### 1. Amazon Web Services (AWS)

    AWS Lambda

**Key features**:
- Fully managed serverless compute service.
- Supports multiple languages including Node.js, Python, Ruby, Java, Go, and .NET Core.
- Automatically scales based on incoming request volume.
- Pay-as-you-go pricing model based on number of requests and compute time.
- Integrated with other AWS services like S3, DynamoDB, and API Gateway.
- Provides AWS Lambda Layers for code sharing across functions.
- Built-in monitoring and logging via Amazon CloudWatch.
- Supports container image deployment for larger workloads.

    AWS Fargate

**Key Features**:
- Serverless compute engine for containers.
- Integrates with Amazon ECS and EKS.
- No need to provision or manage servers.
- Automatically scales to handle desired workloads.
- Pricing based on vCPU and memory resources consumed.
- Provides IAM roles for tasks to securely access other AWS services.
- Integrated with AWS CloudWatch for logging and monitoring.
- Supports both Linux and Windows containers.

### 2. Google Cloud Platform (GCP)

    Google Cloud Functions

**Key Features**:
- Event-driven serverless compute service.
- Supports languages like JavaScript (Node.js), Python, Go, Java, .NET, and Ruby.
- Scales automatically based on the number of incoming requests.
- Pay-as-you-go pricing model based on compute time and number of invocations.
- Integrated with other GCP services such as Pub/Sub, Cloud Storage, and Firestore.
- Provides built-in monitoring and logging via Google Cloud Monitoring and Logging.
- Supports environment variables for configuration.
- Provides Cloud Functions Framework for local development and testing.

    Google Cloud Run

**Key Features**:
- Fully managed compute platform for running containerized applications.
- Automatically scales from zero to handle your workloads.
- Supports any containerized application regardless of language.
- Pay-as-you-go pricing based on the resources your containers use.
- Integrated with other GCP services like Cloud Build, Pub/Sub, and Firestore.
- Provides custom domains and HTTPS support.
- Built-in monitoring, logging, and tracing via Google Cloud Monitoring, Logging, and Trace.
- Knative-compatible, allowing easy deployment of Kubernetes-based workloads.

### 3. Azure (Microsoft Azure)

    Azure Functions

**Key Features**:
- Event-driven serverless compute service.
- Supports multiple languages including C#, JavaScript, F#, Java, Python, and PowerShell.
- Automatically scales based on demand.
- Consumption-based pricing model, paying only for the resources you consume.
- Integrated with other Azure services such as Azure Event Grid, Storage, and Cosmos DB.
- Provides Azure Functions Premium Plan for enhanced performance and VNET integration.
- Built-in monitoring and diagnostics via Azure Monitor.
- Supports deployment slots for testing in production environments.

    Azure Container Instances (ACI)

**Key Features**:
- Serverless container service for running Docker containers.
- No need to manage underlying virtual machines.
- Instant provisioning and auto-scaling of containers.
- Pay-as-you-go pricing based on vCPU and memory resources consumed.
- Integrated with other Azure services like Azure Virtual Network, Storage, and Log Analytics.
- Supports both Linux and Windows containers.
- Provides secure and isolated environments for running containers.
- Offers ACI connector for Kubernetes to manage ACI containers from AKS.