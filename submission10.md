# Lab 10: Cloud Computing Lab - Artifact Registries and Serverless Computing Platforms
## Anton Buguev, a.buguev@innopolis.university, M23-RO-01

### Task 1. Artifact Registries Research

1. **Amazon Web Services (AWS)** is one of the leading cloud service providers that provides a wide range of services for computing, storage, databases, machine learning, analytics, *etc*. As main fetures AWS offers 
    - variety of services and solutions,
    - extensive network of data centers worldwide,
    - high scalability.

    However, all these features come with a high price and complexity of managing and configuration due to the large number of services.

    As artifact registry AWS provies ***Amazon Elastic Container Registry (ECR)*** that has
    - fully managed Docker container registry,
    - integrated Identity and Access Management (IAM) for security,
    - support for public and private repositories,
    - sclability and high availability.


2. **Google Cloud Platform (GCP)** is suite of cloud computing services that provides a series of modular cloud services including computing, data storage, data analytics, and machine learning, alongside a set of management tools. Main features that GCP provides are
    - strong offerings for big data and machine learning,
    - high-performance global network,
    - smaller prices,
    - simple integration with other Google products.
    
    However, GCP offers fewer services compared to AWS and has smaller ecosystem of third-party tools and services.

    GCP also has artifact registry ***Google Artifact Registry*** which main features are
    - unified repository for container images and other artifacts.
    - support of Docker, Maven, npm, and other formats.
    - integration with Google Cloud’s security and IAM policies.
    - scalable and reliable storage.

3. **Azure (Microsoft Azure)** is the cloud computing platform developed by Microsoft. It offers management, access and development of applications and services to individuals, companies, and governments through its global infrastructure. Azure as well has its own features:
    - convenient integration with Microsoft products and services,
    - support for hybrid cloud environments,
    - large number of data centers worldwide,
    - comprehensive suite of AI and ML services,
    - extensive compliance certifications and strong security features.

    However, just as with AWS, offered services have high price and it may be complex to manage everything.


    Regarding artifact registry Azure has ***Azure Container Registry (ACR)*** which main features are
    - managed Docker container registry service,
    - integrated with Azure Active Directory for security,
    - supports geo-replication for high availability,
    - automated container building and patching.

#### Concluding we can say that each of these cloud providers offer robust artifact registry services with their own features and benefits that can be applied to different needs and integrations, making it easier for developers to manage and deploy their applications.

### Task 2. Serverless Computing Platform Research.

1. **AWS Lambda (by AWS)** allows you to run code without provisioning or managing servers. You pay only for the compute time you consume. Main features that AWS Lambda provides:
    - automatically run code in response to events like changes to data, shifts in system state, or user actions,
    - multiple language support such as Node.js, Python, Ruby, Java, Go, and .NET Core,
    - simple integration with other AWS services (e.g., S3, DynamoDB, Kinesis, API Gateway),
    - automatic scaling by running code in response to each trigger,
    - managing of how many instances of a function can run simultaneously,
    - integration with AWS CloudWatch for monitoring and logging.

2. **Google Cloud Functions (by GCP)** is a lightweight, event-driven compute solution for developers to create single-purpose, standalone functions that respond to cloud events. Main features that Google Cloud Functions provides:
    - triggered by various events from Google Cloud services, Firebase, and third-party services,
    - multiple language support such as Node.js, Python, Go, Java, and .NET Core,
    - automatically scaling up and down based on the number of incoming requests,
    - seamles integration with Google Cloud services like Cloud Storage, Pub/Sub, Firestore, and more,
    - integrated with Google Cloud’s operations suite (formerly Stackdriver) for monitoring and logging,
    - integrated with Google Cloud IAM for access control.

3. **Azure Functions (by Azure)** is a serverless compute service that enables you to run event-triggered code without having to explicitly provision or manage infrastructure. Main features that Azure Functions provides:
    - can be triggered by HTTP requests, timers, events from Azure services, or third-party services,
    - multiple language support such as C#, Java, JavaScript, Python, PowerShell, and TypeScript,
    - automatic scaling based on demand, handling thousands of concurrent function executions,
    - deep integration with other Azure services like Blob Storage, Cosmos DB, Event Hubs, Service Bus, and more,
    - integrated with Azure Monitor for logging, metrics, and diagnostics,
    - integrated with Azure Active Directory for access control and security.

#### Concluding we can say that each platform provides a robust set of features for running serverless applications, catering to different programming languages, integration needs, and scaling requirements.