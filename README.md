# ![aws](https://github.com/julien-muke/Search-Engine-Website-using-AWS/assets/110755734/01cd6124-8014-4baa-a5fe-bd227844d263)     Deploy Docker Container to AWS ECS Automatically with CI CD Pipeline.


## <a name="introduction">🤖 Introduction</a>

Deploying Docker containers to Amazon Elastic Container Service (ECS) automatically with a CI/CD pipeline streamlines the process of managing and scaling applications in the cloud. This approach leverages the power of continuous integration and continuous deployment to ensure that updates and new features are seamlessly integrated and deployed with minimal manual intervention. By automating the deployment process, developers can focus more on coding and less on operational tasks, improving efficiency and reducing the risk of errors. Utilizing tools like AWS CodePipeline, CodeBuild, and CodeDeploy, alongside Docker and ECS, creates a robust and scalable infrastructure that supports rapid development and reliable application delivery.


## <a name="design">📐 Architecture Diagram</a>

![Docker Image-2](https://github.com/julien-muke/nodejs-docker-aws-ecs/assets/110755734/121e371a-3b6f-4a7c-a20d-34a05b2af90a)


## Use Case: Deploying Web Application on Amazon ECS.

Imagine you are developing a basic web application, and you want to deploy it using Amazon ECS. Example: Imagine a simple Node.j  application that displays "Hello, World!" on a webpage. The Dockerfile could specify the Node.js base image and install any required dependencies. You'd then build and push the image to ECR. Finally, by creating an ECS service with your task definition, you'd deploy the application on Fargate, making it accessible on the internet.


## <a name="steps">☑️ Steps</a>

The procedure for deploying this architecture on AWS consists of the following steps:

Step 1. Create WebApp Docker Image

Step 2. Create aws-cli user

Step 3. Create & push image to AWS ECR repository

Step 4. Create Security Groups

Step 5. Create AWS ECS Fargate Cluster

Step 6. Create Task Definition

Step 7. Create ECS Service with Application Load Balancer

Step 8 Update Application Load Balancer Security Group


## 📝 Prerequisites

Before you begin, ensure the following prerequisites are met:



* Ensure you have completed the Amazon ECR setup steps. For more information, see [Setting up for Amazon ECR](https://docs.aws.amazon.com/AmazonECR/latest/userguide/get-set-up-for-amazon-ecr.html) in the Amazon Elastic Container Registry User Guide.

* Your user has the required IAM permissions to access and use the Amazon ECR service. For more information, see [Amazon ECR managed policies](https://docs.aws.amazon.com/AmazonECR/latest/userguide/security-iam-awsmanpol.html).

* You have Docker installed. For Docker installation steps for Amazon Linux 2, see [Installing Docker on AL2023](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/create-container-image.html#create-container-image-install-docker). For all other operating systems, see the Docker documentation at [Docker Desktop overview](https://docs.docker.com/desktop/).

* You have the AWS CLI installed and configured. For more information, see [Installing the AWS Command Line Interface](https://docs.aws.amazon.com/cli/latest/userguide/installing.html) in the AWS Command Line Interface User Guide.



## ➡️ Step 1 - Create WebApp Docker Image

Amazon ECS uses Docker images in task definitions to launch containers. Docker is a technology that provides the tools for you to build, run, test, and deploy distributed applications in containers. 

To create a Docker image of a simple web application:

1. Create a file called Dockerfile. A Dockerfile is a manifest that describes the base image to use for your Docker image and what you want installed and running on it. For more information about Dockerfiles.

```bash
touch Dockerfile
```

2. Edit the Dockerfile you just created and add the following content.

```bash
FROM node:alpine

WORKDIR /nodejs-docker-aws-ecs

COPY package.json .

RUN npm install

COPY . .

EXPOSE 3000

CMD [ "node", "app.js" ]
```










## 💰 Cost

All services used are eligible for the AWS Free Tier. However, charges will incur at some point so it's recommended that you shut down resources after completing this tutorial.


## Conclusion

In this blog post, we have provided a step-by-step guide on how to develop and deploy a basic web application on Amazon ECS using Fargate. By following these steps, you can learn the basics of ECS and Fargate and get started with deploying containerized applications on AWS. This approach offers scalability, reliability, and cost-effectiveness for managing containerized workloads in the cloud.