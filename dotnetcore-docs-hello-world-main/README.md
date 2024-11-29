# .NET 8 Hello World

This sample demonstrates a tiny Hello World .NET Core app for [App Service Web App](https://docs.microsoft.com/azure/app-service-web). This sample can be used in a .NET Azure App Service app as well as in a Custom Container Azure App Service app.

## Log in to Azure Container Registry

Using the Azure CLI, log in to the Azure Container Registry (ACR):

```azurecli
az acr login -n <your_registry_name>
```

## Running in a Docker Container

This repository contains 2 Dockerfiles, a Linux container and a Windows container.

### Publish the Windows image to your Registry

To build the Windows image locally and publish to ACR, run the following command:

```docker
docker build -f Dockerfile.windows -t dotnetcore-docs-hello-world-windows . 
docker tag dotnetcore-docs-hello-world-windows <your_registry_name>.azurecr.io/dotnetcore-docs-hello-world-windows:latest
docker push <your_registry_name>.azurecr.io/dotnetcore-docs-hello-world-windows:latest
```

### Publish the Linux image to your Registry

To build the Linux image locally and publish to ACR, run the following command:

```docker
docker build -f Dockerfile.linux -t dotnetcore-docs-hello-world-linux . 
docker tag dotnetcore-docs-hello-world-windows <your_registry_name>.azurecr.io/dotnetcore-docs-hello-world-linux:latest
docker push <your_registry_name>.azurecr.io/dotnetcore-docs-hello-world-linux:latest
```
Project Overview

This project demonstrates the development and deployment of a containerized .NET Core application using Docker, GitHub Actions for CI/CD pipelines, and Azure services. It automates the build, test, and deployment process, ensuring efficient and reliable application delivery to an Azure environment.
Features

    Containerization: Application is packaged into a Docker container for consistent execution across environments.
    GitHub Actions: CI/CD pipelines automate the build, testing, and deployment processes.
    Azure Integration: Application is deployed to an Azure App Service or Azure Kubernetes Service (AKS) for scalable hosting.
    Environment Configuration: Terraform is used to provision Azure resources, ensuring an infrastructure-as-code approach.

Setup Instructions

    Clone the Repository

git clone https://github.com/YourGitHubHandle/DotNet-Core-CI-CD-Azure.git
cd DotNet-Core-CI-CD-Azure

Dockerize the Application

    Build the Docker image locally:

    docker build -t dotnet-core-app .

Run the Application Locally

    docker run -p 8080:80 dotnet-core-app

    Configure GitHub Actions
        Add your Azure credentials as secrets in the repository (AZURE_CREDENTIALS, ACR_LOGIN_SERVER, etc.).
        The CI/CD workflow will handle building the Docker image, pushing it to Azure Container Registry (ACR), and deploying it to the Azure environment.

    Deploy the Application
        Push changes to the repository to trigger the CI/CD pipeline.
        The app will automatically be deployed to the specified Azure resource.

Technologies Used

    Programming Language: .NET Core (C#)
    CI/CD Tools: GitHub Actions
    Containerization: Docker
    Cloud Services: Azure App Service or Azure Kubernetes Service (AKS), Azure Container Registry (ACR)
    Infrastructure as Code: Terraform


# Contributing

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
