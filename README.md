# azure-aks-microservices
This project demonstrates the deployment of a containerized microservices application on Microsoft Azure using Docker, Azure Container Registry, Azure Kubernetes Service, and Terraform. It highlights Infrastructure as Code practices, Kubernetes orchestration, secure database integration, and scalable cloud-native application deployment.


## Project Overview
Project Name:
Azure AKS Microservices Platform

## Description
This project demonstrates deployment of a containerized microservices architecture using Azure cloud-native services and Kubernetes orchestration.

##  The solution includes:
. Frontend web application
. Backend REST API (Flask)
. PostgreSQL database
. Infrastructure provisioning using Terraform
. Container registry using Azure Container Registry
. Container orchestration using Azure Kubernetes Service

## Project Objectives:
. Demonstrate Infrastructure as Code using Terraform
. Implement containerization using Docker
. Deploy microservices using Kubernetes
. Implement persistent database storage
. Demonstrate service-to-service communication
. Provide publicly accessible frontend

## Cloud Services Used:
    Service				                Purpose
Azure Kubernetes Service        Container orchestration
Azure Container Registry	    Container image storage
Azure Disk (CSI)		        Persistent storage
Azure Resource Group		    Resource organization

## Architecture Pattern
This project follows-
. 3-Tier Architecture
. Microservices Deployment
. Cloud Native Design

User Browser
     │
     ▼
Azure LoadBalancer (Frontend Service)
     │
     ▼
Frontend Container (HTML / Nginx)
     │
     ▼
Backend LoadBalancer Service
     │
     ▼
Backend Flask API (AKS Pod)
     │
     ▼
PostgreSQL Service (ClusterIP)
     │
     ▼
PostgreSQL Database Pod
     │
     ▼
Azure Managed Disk (Persistent Storage)


Terraform
   │
   ├── Resource Group
   ├── Azure Container Registry
   └── AKS Cluster


## Technologies Used
Terraform
Docker
Kubernetes
Azure CLI
Flask (Python)
PostgreSQL
Nginx
GitHub
Docker → ACR → AKS → Kubernetes Pods


## azure-aks-microservices/
├── backend
│   ├── Dockerfile
│   ├── app.py
│   └── requirements.txt
│
├── frontend
│   ├── Dockerfile
│   ├── index.html
│   └── health.html
│
├── k8s
│   ├── backend
│   ├── frontend
│   └── database
│
├── terraform
│   ├── main.tf
│   ├── provider.tf
│   ├── variables.tf
│   ├── outputs.tf
│   └── terraform.tfvars
│
├── docs
└── README.md

##  Infrastructure Deployment
Step 1 — Clone Repository
git clone https://github.com/BunmiOrunmbe/azure-aks-microservices.git
cd azure-aks-microservices

### Step 2 — Deploy Azure Infrastructure
cd terraform
terraform init
terraform plan
terraform apply

### Step 3 — Connect To AKS Cluster
az aks get-credentials \
--resource-group aks-microservices-rg \
--name microservices-aks


##  Docker Image Build & Push
### Backend
docker build -t microservicesacr55522.azurecr.io/backend:v1 backend
docker push microservicesacr55522.azurecr.io/backend:v1

### Frontend
docker build -t microservicesacr55522.azurecr.io/frontend:v1 frontend
docker push microservicesacr55522.azurecr.io/frontend:v1

## Kubernetes Deployment
kubectl apply -f k8s/

## Accessing The Application
kubectl get svc

## Database Configuration
. PostgreSQL deployed as Kubernetes Deployment
. Persistent storage using Azure Managed Disk
. Credentials stored securely using Kubernetes Secrets
. Database connected via internal ClusterIP service

## Environment Variables
Backend requires-
POSTGRES_HOST
POSTGRES_DB
POSTGRES_USER
POSTGRES_PASSWORD

## Project Achievements
✔ Fully automated cloud infrastructure deployment
✔ Containerized microservices application
✔ Persistent database storage implementation
✔ Secure secrets management
✔ Public cloud service exposure via LoadBalancer
✔ AKS orchestration with rolling deployments

## 🧪 Testing
⚠️ The LoadBalancer IP may change if the service is recreated.

### frotend Health Check
http://20.116.241.112 

### Backend Health Check
 http://20.116.241.112/

### Database Connectivity Test
 http://20.116.241.112/db



👩‍💻 Author:
Bunmi Orunmbe
Cloud | DevOps | Infrastructure Automation | Kubernetes