# Cloud Computing Lab - Artifact Registries and Serverless Computing Platforms

## Task 1: Artifact Registries Research

### AWS

- **AWS CodeArtifact**: A fully managed artifact repository service that allows you to store, publish, and share software packages. It supports popular package managers and build tools like Maven, Gradle, npm, Yarn, Twine, pip, NuGet, and SwiftPM.

### GCP

- **Google Cloud Artifact Registry**: A single place for your organization to manage container images and language packages such as Maven and npm. It is fully integrated with Google Cloud's tooling and runtimes.

### Azure

- **Azure Container Registry**: Provides users with direct control of their container content, with integrated authentication, geo-replication supporting global distribution and reliability for network-close deployments.
- **Azure Artifacts**: Allows developers to publish packages to their feeds and share them within their team, across organizations, and even publicly across the internet. It supports package types: NuGet, npm, Python, Maven, Cargo, and Universal Packages.

## Artifact Registries comparison in table

| Cloud Provider | Service Name                                                                                     | Key Features                                                                                                                                                                                                                           |
| -------------- | ------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AWS            | [Amazon Elastic Container Registry (ECR)](https://aws.amazon.com/ecr/)                           | - Fully managed Docker container registry<br>- Integrates with ECS, EKS, and Lambda<br>- Supports private repositories<br>- Lifecycle policies for image management<br>- Encryption at rest and in transit                             |
| GCP            | [Artifact Registry](https://cloud.google.com/artifact-registry)                                  | - Universal package management<br>- Supports Docker images, Maven/Gradle artifacts, npm packages, and more<br>- Integrated with Google Cloud Build and Cloud Deploy<br>- Fine-grained access controls<br>- Vulnerability scanning      |
| Azure          | [Azure Container Registry (ACR)](https://azure.microsoft.com/en-us/services/container-registry/) | - Managed, private Docker registry service<br>- Geo-replication for multi-region deployments<br>- Integrated with Azure Kubernetes Service (AKS) and Azure DevOps<br>- Content trust for image tag signing<br>- Automated image builds |

## Task 2: Serverless Computing Platform Research

### AWS

- **AWS Lambda**: An event-driven, pay-as-you-go compute service that lets you run code without provisioning or managing servers.

### GCP

- **Google Cloud Functions**: Allows you to build and run applications without having to manage any servers and pay only for the exact amount of resources used.

### Azure

- **Azure Functions**: Allows developers to build and run applications without managing infrastructure. It provides a way to build and deploy serverless apps at scale.

## Serverless Computing Platforms comparison in table

| Cloud Provider | Service Name                                                             | Key Features                                                                                                                                                                                                                           |
| -------------- | ------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AWS            | [AWS Lambda](https://aws.amazon.com/lambda/)                             | - Event-driven, serverless computing<br>- Supports multiple programming languages<br>- Automatic scaling and high availability<br>- Pay-per-use pricing model<br>- Integrates with other AWS services                                  |
| GCP            | [Cloud Functions](https://cloud.google.com/functions)                    | - Event-driven serverless platform<br>- Supports Node.js, Python, Go, Java, and .NET<br>- Automatic scaling and zero infrastructure management<br>- Integrated with Google Cloud services<br>- Pay-only-for-what-you-use pricing       |
| GCP            | [Cloud Run](https://cloud.google.com/run)                                | - Fully managed serverless platform for containerized applications<br>- Supports any language and library<br>- Automatic scaling to zero<br>- Integration with Cloud Build and Artifact Registry<br>- Pay-per-use pricing model        |
| Azure          | [Azure Functions](https://azure.microsoft.com/en-us/services/functions/) | - Event-driven, serverless compute platform<br>- Supports multiple programming languages<br>- Automatic scaling and load balancing<br>- Integrated with Azure services and external tools<br>- Consumption and Premium plans available |
