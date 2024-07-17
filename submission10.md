## Task 1: Artifact Registries Research

- AWS 
    - Amazon ECR 

        **Key Features**: Docker registry, ECS/EKS/Lambda integration, private repos, vulnerability scans, lifecycle policies. 

        **Pricing**: $0.10/GB/month for storage, $0.09/GB for data transfer (first 10 TB). 
        
        **UI**: AWS Console, CLI, SDKs. 


    - CodeArtifact 
        
        **Key Features**: Maven/npm/Python/NuGet, integrates with CodeBuild/CodePipeline, scalable, secure. 


        **Pricing**: $0.10/GB/month for storage, $0.50 per 100,000 requests. 


        **UI**: AWS Console, CLI, SDKs. 

- GCP 
    - Google Container Registry (GCR) 

        **Key Features**: Docker registry, GKE integration, global replication, vulnerability scans, IAM access control. 


        **Pricing**: $0.026/GB/month for storage, $0.12/GB for data transfer in North America. 


        **UI**: Google Cloud Console, CLI, SDKs. 


    - Google Artifact Registry 

        **Key Features**: Docker/Maven/npm/Python, centralized storage, fine-grained control, Cloud Build integration, automated builds. 


        **Pricing**: $0.10/GB/month for storage, $0.01 per 10,000 requests. 


        **UI**: Google Cloud Console, CLI, SDKs. 


- Azure 
    - Azure Container Registry (ACR) 

        **Key Features**: Docker registry, AKS integration, geo-replication, vulnerability scans, automated tasks. 


        **Pricing**: Basic $5/month, Standard $20/month, Premium $80/month, $0.087/GB for data transfer (first 10 TB). 


        **UI**: Azure Portal, CLI, SDKs. 


    - Azure Artifacts 

        **Key Features**: Maven/npm/NuGet/Python, DevOps integration, scalable, secure, upstream sources, versioning. 


        **Pricing**: Free up to 2 GB, $2/GB/month for additional storage, first 2 GB transfer free; $0.50/GB thereafter. 


        **UI**: Azure DevOps interface, CLI, SDKs. 


### My Take on These Registries 

#### AWS 

ECR: Solid for Docker stuff, integrates well with other AWS services. Prices are decent but watch out for data transfer costs. 

CodeArtifact: Great for multiple package formats, especially if we're deep into AWS tools. Charges per request can add up. 

#### GCP 

GCR: Good for Docker and GKE users. Cheap storage but data transfer is a bit pricey if we're outside North America. 

Artifact Registry: Versatile, works with Docker and other package types. Affordable and integrates nicely with Cloud Build. 

#### Azure 

ACR: Best if we're in the Azure ecosystem, especially with AKS. Pricing is tiered, so we will pick what fits our needs. 

Artifacts: Perfect for DevOps users needing multiple package types. Free tier is generous, but additional storage isn't cheap. 

### Artifact Registries Comparison

#### AWS

1. **Amazon ECR**
   - **Key Features**: Docker registry, ECS/EKS/Lambda integration, private repos, vulnerability scans, lifecycle policies.
   - **Pricing**: $0.10/GB/month for storage, $0.09/GB for data transfer (first 10 TB).
   - **UI**: AWS Console, CLI, SDKs.

2. **AWS CodeArtifact**
   - **Key Features**: Maven/npm/Python/NuGet, integrates with CodeBuild/CodePipeline, scalable, secure.
   - **Pricing**: $0.10/GB/month for storage, $0.50 per 100,000 requests.
   - **UI**: AWS Console, CLI, SDKs.

#### GCP

1. **Google Container Registry (GCR)**
   - **Key Features**: Docker registry, GKE integration, global replication, vulnerability scans, IAM access control.
   - **Pricing**: $0.026/GB/month for storage, $0.12/GB for data transfer in North America.
   - **UI**: Google Cloud Console, CLI, SDKs.

2. **Google Artifact Registry**
   - **Key Features**: Docker/Maven/npm/Python, centralized storage, fine-grained control, Cloud Build integration, automated builds.
   - **Pricing**: $0.10/GB/month for storage, $0.01 per 10,000 requests.
   - **UI**: Google Cloud Console, CLI, SDKs.

#### Azure

1. **Azure Container Registry (ACR)**
   - **Key Features**: Docker registry, AKS integration, geo-replication, vulnerability scans, automated tasks.
   - **Pricing**: Basic $5/month, Standard $20/month, Premium $80/month, $0.087/GB for data transfer (first 10 TB).
   - **UI**: Azure Portal, CLI, SDKs.

2. **Azure Artifacts**
   - **Key Features**: Maven/npm/NuGet/Python, DevOps integration, scalable, secure, upstream sources, versioning.
   - **Pricing**: Free up to 2 GB, $2/GB/month for additional storage, first 2 GB transfer free; $0.50/GB thereafter.
   - **UI**: Azure DevOps interface, CLI, SDKs.

### My Take on These Registries

#### AWS
- **ECR**: Solid for Docker stuff, integrates well with other AWS services. Prices are decent but watch out for data transfer costs.
- **CodeArtifact**: Great for multiple package formats, especially if we're deep into AWS tools. Charges per request can add up.

#### GCP
- **GCR**: Good for Docker and GKE users. Cheap storage but data transfer is a bit pricey if we're outside North America.
- **Artifact Registry**: Versatile, works with Docker and other package types. Affordable and integrates nicely with Cloud Build.

#### Azure
- **ACR**: Best if we're in the Azure ecosystem, especially with AKS. Pricing is tiered, so we will hypothetically pick what fits our needs.
- **Artifacts**: Perfect for DevOps users needing multiple package types. Free tier is generous, but additional storage isn't cheap.


## Task 2: Serverless Computing Platform Research


### Serverless Computing Platforms Comparison

- **AWS**
    - **AWS Lambda**
        - **Key Features**: Event-driven compute service, supports multiple languages (Node.js, Python, Java, Go, etc.), integrates with S3, DynamoDB, API Gateway, and more, automatic scaling and high availability, pay-per-use pricing model.
        - **Pricing**: Free tier: 1 million requests and 400,000 GB-seconds of compute time per month; $0.20 per 1 million requests thereafter; $0.00001667 per GB-second of compute time.
        - **UI**: AWS Management Console, CLI, SDKs.

    - **AWS Fargate**
        - **Key Features**: Serverless compute engine for containers, works with ECS and EKS, no server management needed, automatic scaling based on demand.
        - **Pricing**: vCPU: $0.04048 per vCPU per hour; Memory: $0.004445 per GB per hour.
        - **UI**: AWS Management Console, CLI, SDKs.

- **GCP**
    - **Google Cloud Functions**
        - **Key Features**: Event-driven compute service for building and connecting cloud services, supports multiple languages (Node.js, Python, Go, etc.), integrated with Cloud Storage, Pub/Sub, Firestore, automatic scaling and high availability.
        - **Pricing**: Free tier: 2 million invocations per month; $0.40 per million invocations thereafter; $0.0000025 per GHz-second, $0.00000028 per MB-second.
        - **UI**: Google Cloud Console, CLI, SDKs.

    - **Google Cloud Run**
        - **Key Features**: Fully managed compute platform for running containerized applications, supports any language and framework via containers, automatic scaling based on traffic, integrated with Google Cloud services and tools.
        - **Pricing**: Free tier: 2 million requests per month; $0.10 per vCPU hour, $0.000024 per GB-second.
        - **UI**: Google Cloud Console, CLI, SDKs.

- **Azure**
    - **Azure Functions**
        - **Key Features**: Event-driven serverless compute service, supports multiple languages (C#, JavaScript, Python, etc.), integrated with Azure services (Blob Storage, Event Grid, Service Bus), automatic scaling and high availability.
        - **Pricing**: Free tier: 1 million requests and 400,000 GB-seconds per month; $0.20 per million executions thereafter; $0.000016 per GB-second of execution time.
        - **UI**: Azure Portal, CLI, SDKs.

    - **Azure Container Instances (ACI)**
        - **Key Features**: Serverless container service for running containers without managing servers, supports Docker containers, rapid startup times and automatic scaling, integrated with Azure Kubernetes Service (AKS).
        - **Pricing**: vCPU: $0.0075 per vCPU per second; Memory: $0.000012 per GB per second.
        - **UI**: Azure Portal, CLI, SDKs.

### My Take on These Serverless Platforms

#### AWS
- **Lambda**: Great for event-driven applications, extensive language support. Pay-per-use is awesome, but compute costs can add up if we're not careful.
- **Fargate**: Perfect for containerized workloads without managing servers. Simple pricing but can get expensive with heavy usage.

#### GCP
- **Cloud Functions**: Easy to use for small functions and integrations, generous free tier. Pricing is competitive, but we need to watch out for compute costs.
- **Cloud Run**: Ideal for containerized apps, flexible language support. Pay-per-use and free tier are nice, but costs can spike with high traffic.

#### Azure
- **Functions**: Solid for event-driven tasks, good language support, integrates well with other Azure services. Free tier is decent, but pricing is similar to AWS.
- **ACI**: Good for running containers without managing servers. Pricing is straightforward but can be pricey for long-running tasks.
