# Lab 10 : Cloud Computing Lab - Artifact Registries and Serverless Computing Platforms


## Task 1: Artifact Registries Research

###  Amazon web services (AWS) artifact registries

#### AWS CodeArtifact
- AWS CodeArtifact allows users to store artifacts using popular package managers and build tools like Maven, Gradle, npm, Yarn, Twine, pip, NuGet, and SwiftPM. It can automatically fetch software packages on demand from public package repositories allowing users to access the latest versions of application dependencies.
#### Key Features
- Consume packages from public artifact repositorie : Users can configure CodeArtifact to fetch software packages from public repositories such as the npm Registry, Maven Central, PyPI etc.
- Publish and share package : Users can use their existing package managers such as npm, pip, yarn, twine, Maven, NuGet, the Gem CLI, Bundler and SwiftPM to publish packages developed within their organization.
- Enable access control and monitoring : AWS CodeArtifact integrates with IAM and AWS CloudTrail, offering control over who can access software packages and visibility into who has access to your software packages. CodeArtifact also integrates with AWS Key Management Service (KMS) for package encryption.
- High availability and durability : AWS CodeArtifact operates in multiple Availability Zones and stores artifact data and metadata in Amazon S3 and Amazon DynamoDB. Encrypted data is redundantly stored across multiple facilities and multiple devices in each facility, making it highly available and highly durable.
#### [Source](https://aws.amazon.com/codeartifact/)

#### Amazon Elastic Container Registry
- Amazon Elastic Container Registry (Amazon ECR) is a fully managed container registry offering high-performance hosting, so users can reliably deploy application images and artifacts anywhere.
#### Key Features
- OCI and Docker support : Amazon ECR supports Open Container Initiative (OCI) standards and the Docker Registry HTTP API V2. This allows users to use Docker CLI commands (e.g., push, pull, list, tag) or their preferred Docker tools to interact with Amazon ECR, maintaining your existing development workflow.
- Public container image and artifact gallery : Users can discover and use container software that vendors, open source projects, and community developers share publicly in the Amazon ECR public gallery.
- Secure, scalable, and reliable.
#### [Source](https://aws.amazon.com/ecr/s)

### Google Cloud Platform (GCP) artifact registries

#### Google Artifact Registry
- Google Artifact Registry is a fully managed service that provides a single place to manage container images and language packages (e.g., npm, Maven). It is a unified solution to store and manage various artifact types.
#### Key Features
- Supports Docker images, Maven packages, npm packages, and more : It is a versatile service that supports a variety of artifact types, including Docker container images, Java packages (Maven), JavaScript packages (npm), and more. This flexibility allows development teams to manage different types of software components in a single, unified repository.
- Integration with Google Kubernetes Engine (GKE) and Cloud Build : It seamlessly integrates with Google Kubernetes Engine (GKE) and Google Cloud Build, enabling streamlined workflows for building, storing, and deploying containerized applications. 
- Fine-grained access control using Google Cloud IAM : Artifact Registry provides fine-grained access control, ensuring that only authorized users and services can access, modify, or deploy artifacts.
- It is Fast, scalable, reliable and secure : Google Artifact Registry is designed to be fast, scalable, reliable, and secure. It leverages Google's robust infrastructure to ensure high performance and availability.
#### [Source](https://cloud.google.com/artifact-registry/docs)

#### Google Container Registry
- Google Container Registry provides secure, private Docker repository storage on Google Cloud Platform (GCP). Users can use gcloud to push repositories to registries, then pull repositories using an HTTP endpoint from any machine, whether it's a Google Compute Engine instance or their own hardware.
#### Key Features
- Docker CLI Integration :Pull container images from Container Registry using the standard Docker command line interface.
- Advanced Authentication : Easily integrate with your favorite continuous integration, continuous delivery, and container orchestration systems with built-in Docker Login support.
- Automated Build Triggers : Automatically build containers on source code or tag changes to a repository in Google Cloud Source Repositories, GitHub, or Bitbucke
#### [Source](https://console.cloud.google.com/marketplace/product/google-cloud-platform/container-registry?project=automated-style-401009s)

###  Microsoft Azure artifact registries

#### Azure Container Registry (ACR)
- A registry of Docker and Open Container Initiative (OCI) images, with support for all OCI artifacts.
#### Key Features
- Geo-replication to efficiently manage a single registry across multiple regions
- OCI artifact repository for adding Helm charts, Singularity support, and new OCI artifact-supported formats
- Automated container building and patching including base image updates and task scheduling
- Integrated security with Azure Active Directory (Azure AD) authentication, role-based access control, Docker Content Trust, and virtual network integration
#### [Source](https://azure.microsoft.com/en-us/products/container-registry)

#### Azure artifacts
- A service for Creating, hosting, and sharing packages with your team.
#### Key Features
- Share code efficiently : Easily share code across small teams and large enterprises.
- Manage all package types : Get universal artifact management for Maven, npm, NuGet, and Python.
- Add packages to any pipeline : Share packages, and use built-in CI/CD, versioning, and testing.
#### [Source](https://azure.microsoft.com/en-us/products/devops/artifactsy)

## Task 2: Serverless Computing Platform Research

###  Amazon Web Services (AWS) Serverless Computing Platforms

#### AWS Lambda
- AWS Lambda is a serverless compute service that lets users run code without provisioning or managing servers.
#### Key Features
- Extend other AWS services with custom logic : AWS Lambda allows you to add custom logic to AWS resources such as Amazon S3 buckets and Amazon DynamoDB tables, so you can easily apply compute to data as it enters or moves through the cloud.
- Build custom backend services : You can use AWS Lambda to create new backend application services triggered on demand using the Lambda application programming interface (API) or custom API endpoints built using Amazon API Gateway.
- Built-in fault tolerance : AWS Lambda maintains compute capacity across multiple Availability Zones (AZs) in each AWS Region to help protect your code against individual machine or data center facility failures. Both AWS Lambda and the functions running on the service deliver predictable and reliable operational performance. 
- Automatic scaling : AWS Lambda invokes your code only when needed, and automatically scales to support the rate of incoming requests without any manual configuration. There is no limit to the number of requests your code can handle
#### [Source](https://aws.amazon.com/lambda/)

#### AWS Fargate
- AWS Fargate is a serverless compute engine for containers that works with both Amazon ECS and Amazon EKS. It allows you to run containers without having to manage the underlying infrastructure.
#### Key Features
- Serverless compute for containers: AWS Fargate manages capacity needs, operating system (OS) updates, compliance requirements, resiliency, and more, freeing you to focus on applications, not servers.
- Seamless scaling with serverless compute : Respond to changes in demand seamlessly by dynamically scaling capacity to reduce wasted resources while ensuring application availability.
- Virtualization boundary for containerized workloads : For sensitive, multi-tenant, or regulated containerized workloads, AWS Fargate provides a secure virtualization boundary between every Amazon ECS task or Amazon EKS pod. Each task / pod is deployed on to a dedicated single use, single tenant piece of compute, providing secure isolation between workloads.
#### [Source](https://aws.amazon.com/fargate/)

### Google Serverless Computing Platforms

#### Google Cloud Functions
-  Google Cloud Functions is a lightweight, serverless compute solution for event-driven applications. It allows you to run your code in response to events without provisioning or managing servers.
#### Key Features
- Simplified developer experience and increased developer velocity : Cloud Functions has a simple and intuitive developer experience. Just write your code and let Google Cloud handle the operational infrastructure.
- Connects and extends services to build complex applications : Cloud Functions lets you treat all Google and third-party cloud services as building blocks. Connect and extend them with code, and rapidly move from concept to production with end-to-end solutions and complex workflows.
- Develop locally, scale globally : Serve users from zero to planet-scale without even thinking about any infrastructure. Cloud Functions automatically manages and scales underlying infrastructure with the size of workload.
- No server management : Deploy your code and let Google run and scale it for you. Cloud Functions abstracts away all the underlying infrastructure, so that you can focus on your code and build applications faster than ever before.
#### [Source](https://cloud.google.com/functions?hl=en)

### Google cloud run
#### Key Features
- Any language, any library, any binary : Users can write code using their favorite language, framework, and libraries, package it up as a container deploy it, and their app will be live and provided with everything it needs to run in production.
- Fast autoscaling : Cloud Run automatically scales your containers up and down from zero.
- Automatically build container images from your source : Cloud Run can also automate how you get to production, using buildpacks to enable you to deploy directly from source—without having to install Docker on your machine.
- Run scheduled jobs to completion : Cloud Run jobs allow you to perform batch processing, with instances running in parallel.
#### [Source](https://cloud.google.com/run?hl=en)

###  Microsoft Azure Serverless Computing Platforms

### Azure Functions
- Azure Functions is a serverless compute service that enables you to run event-driven code without having to manage infrastructure.
#### Key Features
- Supports various programming languages including C#, Java, JavaScript, Python, and PowerShell.
- Triggers from a variety of sources, including HTTP requests, timers, Azure services, and third-party services.
- Integration with Azure DevOps, GitHub, and other CI/CD tools.
- Built-in monitoring and logging with Azure Monitor.
#### [Source](https://azure.microsoft.com/en-us/products/functions#ProductOverview)

### Azure Container Instances
- Azure Container Instances is a serverless container service that allows you to run containers without managing the underlying infrastructure. It offers rapid startup and isolated environments for each container.
#### Key Features
- Run containers without managing servers : By running your workloads in Azure Container Instances (ACI), you can focus on designing and building your applications instead of managing the infrastructure that runs them.
- Fast deployment of containers with per-second billing.
- Integration with other Azure services such as Azure Kubernetes Service (AKS).
- Provides secure networking and environment isolation.
#### [Source](https://azure.microsoft.com/en-us/products/container-instances#overview)



