# Lab10

## Task 1

Artifact registry essentially is a server that stores all the packages that you have produced in a single place. The three most popular solutions are provided by [AWS](https://docs.aws.amazon.com/codeartifact/latest/ug/welcome.html), [GCP](https://cloud.google.com/artifact-registry/docs/overview) and [Azure](https://learn.microsoft.com/en-us/azure/devops/artifacts/?view=azure-devops). They provide a similar service and differs mostly in supported packages, CLI tools and pricing. However, all of artifacts registry mentioned support generic type of packages and could substitute each other. All the supported packages are listed down below as well as tools names.

1. AWS - CodeArtifact
    - Cargo
    - Swift 
    - Maven
    - npm
    - NuGet
    - Python
    - Ruby
    - generic
2. GCP - Artifact Registry
    - Docker Images
    - Go modules
    - Helm charts
    - Java Packages
    - Python
    - Apt
    - RPM
    - generic
3. Azure - Artifacts
    - Maven
    - npm
    - NuGet
    - Python
    - dotnet
    - Gradle
    - Cargo
    - generic

## Task 2

Serverless computing is basically a way to create a backend without creating it by yourself. In all cases you outsource the infrastructure part to the third-party company. And in most cases AWS, GCP and Azure provide a set of tools in order to manage you serverless computing. Down below services and short descriptions are listed for each provider

1. [AWS](https://aws.amazon.com/serverless/getting-started/?nc=sn&loc=2&serverless.sort-by=item.additionalFields.createdDate&serverless.sort-order=desc)
    - Amazon API Gateway - Define you API
    - Amazon EventBridge - Bus/Data channel between applications and AWS services
    - Amazon Simple Notification Service - Backend for providing notifications, such as emails, messages/ push notifications, etc.,to the customers 
    - Amazon Simple Queue Service - queue for application scaling and load distribution
    - AWS Fargate - Container runner
    - AWS Lambda - A functions that executes custom code
    - AWS Serverless Application Model - Framework for creating a serverless applications (form the documentation it is mostly a guidelines of how to use tools listed above)
    - AWS Step Functions - coordinates the parts of serverless application
2. [GPC](https://cloud.google.com/serverless/?hl=en)
    - Cloud Run - Container runner or it could use source based deployment for Go, Node.js, Python, Java, .NET Core, Ruby
    - Cloud Run functions - API definition
3. [Azure](https://learn.microsoft.com/en-us/azure/logic-apps/logic-apps-serverless-overview)
    - Azure Functions - A service that executes some scripts written in C#, Java, JavaScript, PowerShell, Python, and TypeScript
    - Azure Logic Apps - A serverless application workflow configuration tool that defines which Azure functions would be used and what triggers would trigger the computing