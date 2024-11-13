# Cloud Computing Lab - Artifact Registries and Serverless Computing Platforms

In this lab assignment, you will research and compare artifact registries and serverless computing platforms in AWS, GCP, and Azure. You will document your findings in a single Markdown file, providing information on popular artifact registries and the best serverless computing platforms in each cloud platform. Follow the tasks below to complete the lab assignment.

## Task 1: Artifact Registries Research

### **What is an artifact registry?**:
   To begin with we need to understand what is an artifact registry and why we need them.  
   Artifact in IT context are some products as results of compilation, building or creation of some code base. These are the good examples of artifacts:  

  - Program installers (.exe, .apk, etc)
  - Docker containers
  - Prebuild libraries
  - Packages

   So, since we have different artifacts, we need to store them. This is the reason why we might need Artifact Registries. Their main tasks:
   - Storing artifacts in the cloud
   - Version control of artifacts
   - Security
   - Integration with CI/CD.

   And now we need to find out which Artifact Registry is better for our task by comparing their key features. To begin with, as with the whole cloud infrastructure, we have 3 main players:
   - AWS (Amazon)
   - Google
   - Azure (Microsoft)

### Now let's look at them closer.

1) **AWS CodeArtifact**
    - Integration with other AWS services. Which is quite important for some big companies and projects since AWS is the biggest (if I am not mistaken) Cloud ecosystem currently.
    - Security through good accessibility control. 
    - Publishing and spreading of packages is made as simple as possible.
    - Pay-as-you-go pricing

2) **GCP Artifact Registries**
    - Integration with Google Cloud services
    - Centralized storage for artifacts and dependencies. It makes working with it easier due to the unified interface.
    - High-level security

3) **Azure Container Registry**
    - Integration with other Microsoft products.
    - Geo-replication. It makes sharing your product easier and smoother all around the world.
    - Good security measures, including Private Link.
    - Supports all types of files.

## Task 2: Serverless Computing Platform Research

### What is Serverless Computing Platforms

Serverless computing platforms are the platforms which allow developers to run server-side tasks (like CI/CD, deployment, heavy compilation) to the cloud without the need to manage it. So, you don't need to hire special server admin. It is not the replacement of the servers, but can be applicable in some tasks.

### Now about the big-3:
1) **AWS Lambda**
    - Integration with other AWS services.
    - Automatic Scaling, allowing to not think about the future scaling of a project.
    - Very good resource management settings. You can set up almost everything as you want, making it very flexible for almost any task.
    - Pay-as-you-go pricing

2) **Google Cloud Functions**
    - Low latency is one of the main goal the Google team tries to achieve. It can be crucial for some tasks.
    - Fast deployment. This is another priority the team is seeking. Quite good for small- and middle-sized projects.
    - Big variety of very useful and easy-to-use monitoring tools.
    - Paying only for the resources taken for your tasks. Also free-to-use for some very liht workloa, which is basically free to implement, pay to use paying system.

3) **Azure Functions**
    - Durable Functions. This allows to create stateful workflows, which makes the service even more powerful.
    - Huge variety of triggers and bindings to choose.
    - Pay-as-you-go pricing