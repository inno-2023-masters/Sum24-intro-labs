# Submission for lab 10

<div style="text-align: center;">
  <img src="/Resources/1.png" alt="Image 1" style="display: inline-block; margin: 0 10px;" height="120">
  <img src="/Resources/2.png" alt="Image 2" style="display: inline-block; margin: 0 10px;" height="120">
  <img src="/Resources/3.png" alt="Image 3" style="display: inline-block; margin: 0 10px;" height="120">
</div>

## Task 1

### AWS - **Elastic Container Registry (ECR)**

**Key Features:**

- **Fully Managed:** AWS ECR is a fully managed container image registry that simplifies storing, managing, and deploying Docker container images.
- **Integration with AWS Services:** Seamlessly integrates with Amazon ECS, Amazon EKS, and AWS Lambda, simplifying the deployment process.
- **Security:** Supports AWS Identity and Access Management (IAM) for managing access permissions and integrates with AWS Key Management Service (KMS) for encrypting images at rest.
- **Performance:** High availability and scalability, ensuring low-latency access to container images.

### GCP - **Artifact Registry**

**Key Features:**

- **Unified Repository:** Manages both container images and language packages (e.g., Maven, npm) in a single repository, unlike the older Container Registry, which only supported container images.
- **Security:** Offers fine-grained access control with Cloud IAM and built-in vulnerability scanning.
- **Seamless Integration:** Integrates well with Google Cloud’s CI/CD tools such as Cloud Build, and supports native artifact protocols.
- **High Availability:** Provides regional and multi-regional options to ensure low latency and high availability.

### Azure - **Azure Container Registry (ACR)**

**Key Features:**

- **Fully Managed:** Provides a fully managed Docker container registry service that simplifies development to deployment workflows.
- **Integration with Azure Services:** Works seamlessly with Azure Kubernetes Service (AKS) and Azure DevOps for CI/CD pipelines.
- **Security and Compliance:** Offers integration with Azure Active Directory (AD) for role-based access control (RBAC) and supports content trust for image signing and verification.
- **Georeplication:** Supports geo-replication to manage a single registry across multiple regions, improving performance and availability.

## Task 2

### AWS - **AWS Lambda**

**Key Features:**

- **Language Support:** Supports Node.js, Python, Java, C#, and Go.
- **Integration:** Seamlessly integrates with other AWS services such as S3, DynamoDB, and API Gateway.
- **Scaling:** Automatically scales the application by running code in response to each trigger. It can handle up to 1,000 concurrent executions per region by default, which can be increased.
- **Cold Start Mitigation:** Offers provisioned concurrency to reduce cold start times.
- **Execution Time:** Supports a maximum execution time of up to 15 minutes.
- **Security:** Leverages AWS Identity and Access Management (IAM) for permissions and access control.

### Azure - **Azure Functions**

**Key Features:**

- **Language Support:** Fully supports C#, F#, Java, JavaScript, PowerShell, Python, and TypeScript. Additionally, experimental support is available for languages like PHP and Bash.
- **Stateful Functions:** Features Durable Functions to allow for stateful function executions.
- **Integration:** Integrates well with Microsoft services and tools, including Visual Studio, Azure DevOps, and GitHub.
- **Scaling:** Automatically scales based on demand and can handle high concurrency without predefined limits.
- **Execution Time:** Maximum execution time of 5 minutes on the Consumption plan and up to 30 minutes on Premium and Dedicated plans.
- **Security:** Supports Azure Active Directory for authentication and role-based access control.

### GCP - **Google Cloud Functions**

**Key Features:**

- **Language Support:** Primarily supports JavaScript (Node.js), but also supports Python, Go, Java, C#, F#, and Ruby through custom runtimes.
- **Integration:** Integrates seamlessly with other Google Cloud services like BigQuery, Pub/Sub, and Firestore.
- **Scaling:** Automatically scales up and down based on load with no predefined concurrency limits.
- **Cold Start Mitigation:** Generally has faster cold start times compared to other platforms.
- **Execution Time:** Supports a maximum execution time of up to 9 minutes.
- **Security:** Utilizes Google Cloud IAM for access control and management.
