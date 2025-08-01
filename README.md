# Deploying microservice applications in AKS using 

    Infra deploy: Azure Devops Infra Pipeline with Bicep
                  Bicep files in DevOps Artifact

    Docker build and push images to ACR: Azure Build Pipeline

    k8s manifests: DevOps Publish Artifact
    
    App deploy: kubectl Apply in Azure Devops App Pipeline

Prerequisites

    A valid Azure subscription : https://portal.azure.com/

    Azure CLI : https://learn.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest

    kubectl: https://kubernetes.io/docs/tasks/tools/

    bash shell: Most Linux/macOS systems already have this. For Windows, use Git Bash or WSL: https://www.atlassian.com/git/tutorials/git-bash

    Docker Desktop for building and pushing images locally: https://docs.docker.com/desktop/

    Install Bicep: https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/install

# Login to Azure

    az login
    az account set --subscription=<subscriptionId>
    az account show

# Show existing resources

    az resource list

# Azure Identity 

    Create Service Principal (app reg) or Managed Identity for Azure DevOps to authenticate with Azure

# Configure Azure DevOps

    Create Organization, Project and Permissions

# Azure DevOps Service Connection

    Create azure DevOps Service Connection to Azure (ARM) for Infrastructure Pipelines

# Docker Registry Service Connection

    Create azure DevOps Docker Registry Service Connection to ACR

# Kubernetes Service Connection

    Kubernetes Service Connection to deploy using kubectl or Helm

# Configure and run the Infra Pipeline (bicep)

    infra-pipeline.yml

# Connect to cluster

    RESOURCE_GROUP="rg-onlinestore-dev-uksouth-001"
    AKS_NAME="aks-onlinestore-dev-uksouth-001"

    az aks get-credentials --resource-group $(RESOURCE_GROUP) --name $(AKS_NAME)

# Short name for kubectl

    alias k=kubectl

# Show all existing objects

    k get all

# Configure and run the Order Build and Deploy Pipeline

    order-pipeline.yaml

# Configure and run the Product Build and Deploy Pipeline

    product-pipeline.yaml

# Configure and run the store front Build and Deploy Pipeline
 
    store-front-pipeline.yaml

# Configure and run the rabbitmq Deploy Pipeline

    rabbitmq-pipeline.yaml

# Write Kubernetes YAML Manifests for the applicatons

    configmap.yml
    order-deployment.yml
    order-service.yml
    product-deployment.yml
    product-service.yml
    store-front-deployment.yml
    store-front-service.yml
    rabbitmq-deployment.yml
    rabbitmq-service.yml

# Verify the Deployment

    k get pods
    k get services
    Browse the app using http://<LoadBalancer public IP>:80

# Clean the Azure resources

    az group delete --name rg-onlinestore-dev-uksouth-001 --yes --no-wait