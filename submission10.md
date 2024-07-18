
# Cloud Computing Lab - Artifact Registries and Serverless Computing Platforms

## Task 1: Artifact Registries Research
1. **AWS** *Amazon Elastic Container Registry (ECR):* This service from AWS is a managed Docker container registry that simplifies the storage, management, and deployment of Docker container images for developers.

 - Key features include:

     - Fully-managed infrastructure for storing and managing container images.
     - Seamless integration with Amazon ECS and Amazon EKS, supporting all Docker CLI commands.
     - Secure, scalable, and reliable registry for Docker or Open Container Initiative (OCI) images.
     - Image scanning capability to identify vulnerabilities in container images.

2. **GCP** *Google Cloud's Artifact Registry:* Provides a unified place for managing packages and container images.

    - Key features include:

      - Supports Docker and OCI formats for container images and popular package formats like Maven and npm.
      - Facilitates end-to-end artifact management with integration into services like Cloud Build and Google Kubernetes Engine (GKE).
      - Vulnerability scanning for container images to ensure secure deployments.
      - Fine-grained access control and detailed audit logging.

3. **Azure** *Azure Container Registry (ACR):* Azure's solution for artifact registry management.

    - Key features include:

        - Storage for Docker and Open Container Initiative (OCI) images.
        - Integration with Azure DevOps, Azure Kubernetes Service (AKS), Docker CLI, Helm, and more.
        - Geo-replication to manage a single registry across multiple regions.
        - Automated tasks for Docker file building and OS/framework patching.

## Task 2: Serverless Computing Platform Research
1. **AWS** *AWS Lambda:* AWS’s serverless computing platform.

    - Key features include:

        - Automatically scales applications based on incoming request traffic.
        - Billing is based on compute time used.
        - Supports code in Node.js, Python, Java, Go, .NET, Ruby, and custom runtimes.
        - Integrated with other AWS services for building complex applications.

2. **GCP** *Google Cloud Functions:* The serverless execution environment provided by Google Cloud.

    - Key features include:

        - Executes code in response to events, such as changes in Firebase, new Pub/Sub messages, or HTTP requests.
        - Auto-scaling based on incoming events.
        - Supports Node.js, Python, and Go.
        - Integration with Google Cloud Pub/Sub and Google Cloud Storage.

3. **Azure** *Azure Functions:* Microsoft's serverless computing service.

    - Key features include:

        - Reduces the need for extensive code, infrastructure maintenance, and costs.
        - Supports languages like C#, Java, JavaScript, TypeScript, and Python.
        - Integrated with Azure DevOps, GitHub, and other popular services.
        - Offers durable functions to define workflows in code.
