# Task 1
## Artifact Registries

### AWS: Amazon Elastic Container Registry (ECR)
- **Overview**: Amazon ECR is a fully managed Docker container registry that makes it easy for developers to store, manage, and deploy Docker container images.
- **Key Features**:
  - Fully integrated with Amazon Elastic Container Service (ECS) and Kubernetes (EKS).
  - Supports Docker CLI, allowing easy push and pull of images.
  - Integrated with AWS Identity and Access Management (IAM) for fine-grained access control.
  - Scalable and secure storage for container images.

[Reference](https://aws.amazon.com/ecr/)

### GCP: Google Artifact Registry
- **Overview**: Google Artifact Registry is a unified repository manager for various types of artifacts, including container images and language-specific artifacts.
- **Key Features**:
  - Supports multiple artifact formats: Docker images, Maven, npm, and more.
  - Seamless integration with Google Kubernetes Engine (GKE) and Cloud Build.
  - Fine-grained access control using Google Cloud IAM.
  - Vulnerability scanning for container images.

[Reference](https://cloud.google.com/artifact-registry)

### Azure: Azure Container Registry (ACR)
- **Overview**: Azure Container Registry is a managed Docker container registry service used to store and manage private Docker container images.
- **Key Features**:
  - Integration with Azure Kubernetes Service (AKS) and other Azure services.
  - Geo-replication for managing a single registry across multiple regions.
  - Content trust for image signing and verification.
  - Advanced security features including Azure Active Directory (AAD) integration and image vulnerability scanning.

[Reference](https://azure.microsoft.com/en-us/services/container-registry/)

# Task 2

## Serverless Computing Platforms

### AWS: AWS Lambda
- **Overview**: AWS Lambda is a serverless compute service that lets you run code without provisioning or managing servers.
- **Key Features**:
  - Supports multiple programming languages, including Node.js, Python, Java, Go, and C#.
  - Automatic scaling with subsecond metering.
  - Integrated with other AWS services like DynamoDB, S3, and API Gateway.
  - Provides concurrency and scaling controls.

[Reference]https://aws.amazon.com/lambda/)

### GCP: Google Cloud Functions
- **Overview**: Google Cloud Functions is a lightweight, event-driven compute service that allows you to run your code in response to events.
- **Key Features**:
  - Supports multiple languages including Node.js, Python, Go, and Java.
  - Automatic scaling and management.
  - Integrated with Google Cloud services like Pub/Sub, Cloud Storage, and Firestore.
  - Provides built-in security at role and instance level.

[Reference](https://cloud.google.com/functions)

### Azure: Azure Functions
- **Overview**: Azure Functions is a serverless compute service that enables you to run event-triggered code without having to explicitly provision or manage infrastructure.
- **Key Features**:
  - Supports a variety of languages including C#, Java, JavaScript, Python, and PowerShell.
  - Built-in integration with Azure services and third-party services.
  - Scales automatically based on demand.
  - Provides a range of triggers including HTTP requests, timers, and messages from Azure services.

[Reference](https://azure.microsoft.com/en-us/services/functions/)
