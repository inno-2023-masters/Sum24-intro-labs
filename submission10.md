# Lab 10

## Task 1

To identify and document the most popular artifact registries in AWS, GCP, and Azure, I will start by researching the respective services offered by each cloud provider. Here are some popular artifact registries in each platform:

### AWS Artifact Registries:
- **Amazon Elastic Container Registry (ECR)**:
  - Secure and scalable container image registry.
  - Integrates seamlessly with Amazon ECS, EKS, and Docker CLI.
  - Supports private container image repositories.
  
- **AWS CodeArtifact**:
  - Fully managed software package repository service.
  - Supports popular package formats like npm, Maven, PyPI, and others.
  - Provides centralized management of dependencies.

### GCP Artifact Registries:
- **Google Container Registry (GCR)**:
  - Managed Docker container image storage.
  - Integrates well with Google Kubernetes Engine (GKE) and other Google Cloud services.
  - Supports private container image repositories.

- **Google Cloud Storage**:
  - Not specifically an artifact registry but widely used for storing various types of artifacts.
  - Scalable object storage with strong consistency and global edge-caching.

### Azure Artifact Registries:
- **Azure Container Registry (ACR)**:
  - Private Docker container registry that supports Azure Kubernetes Service (AKS) and other Azure services.
  - Integrates with Azure DevOps for CI/CD pipelines.
  - Provides geo-replication for faster container pulls.

- **Azure Artifacts**:
  - Universal package repository for hosting NuGet, npm, Maven, and other packages.
  - Supports multiple feeds for organizing packages and artifacts.
  - Integrates with Azure Pipelines for artifact management.

## Task 2

To identify and document the best serverless computing platforms in AWS, GCP, and Azure, I will need to research the services offered by each cloud provider. Here is an overview of some of the popular serverless computing platforms available on AWS, Google Cloud Platform (GCP), and Microsoft Azure:

### AWS (Amazon Web Services)
1. AWS Lambda
   - Key Features:
     - Pay-as-you-go pricing model.
     - Supports multiple programming languages like Node.js, Python, Java, and more.
     - Integrates with other AWS services for event-driven architecture.
     - Automatic scaling based on incoming traffic.
     - Supports triggers from various sources like API Gateway, S3, DynamoDB, etc.

2. Amazon API Gateway
   - Key Features:
     - Fully managed service to create, publish, maintain, monitor, and secure APIs.
     - Integrates with Lambda for serverless API endpoints.
     - Supports RESTful APIs and WebSocket APIs.
     - Provides features like throttling, caching, and request validation.

### GCP (Google Cloud Platform)
1. Google Cloud Functions
   - Key Features:
     - Event-driven serverless functions.
     - Supports multiple programming languages including Node.js, Python, Go, and more.
     - Automatically scales based on traffic.
     - Integrates with other GCP services like Cloud Storage, Pub/Sub, Firestore, etc.
     - Provides a free tier for usage.

2. Google Cloud Run
   - Key Features:
     - Serverless containers platform.
     - Allows running stateless containers on a fully managed environment.
     - Supports both HTTP and gRPC requests.
     - Autoscaling based on incoming requests.
     - Can be used with Cloud Build for continuous deployment.

### Azure
1. Azure Functions
   - Key Features:
     - Event-driven serverless compute service.
     - Supports multiple programming languages such as C#, JavaScript, Python, etc.
     - Integrates with other Azure services like Blob Storage, Event Grid, Cosmos DB, etc.
     - Provides triggers from various sources like HTTP requests, timers, queues, etc.
     - Supports durable functions for orchestrating workflows.

2. Azure Logic Apps
   - Key Features:
     - Visual workflow automation platform.
     - Allows building workflows with a drag-and-drop interface.
     - Integrates with over 200 connectors for various services.
     - Supports conditional logic, loops, and error handling.
     - Provides monitoring and analytics for workflows.
