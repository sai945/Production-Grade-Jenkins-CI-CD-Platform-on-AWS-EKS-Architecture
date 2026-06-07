Architecture

GitHub
   │
   ▼
GitHub Webhook
   │
   ▼
Jenkins Controller (EKS)
   │
   ▼
Dynamic Jenkins Agents (Kubernetes Pods)
   │
   ├── SonarQube
   ├── Trivy
   ├── Docker Build
   └── Push to ECR
          │
          ▼
       Amazon EKS
          │
          ▼
Application Deployment

Monitoring:
Prometheus + Grafana

Logging:
EFK / OpenSearch

Notifications:
Slack

Infrastructure:
Terraform


--------------------------------------------------------

Phase 1: Infrastructure 
AWS Resources
VPC
Public & Private Subnets
NAT Gateway
EKS Cluster
Node Groups
ECR Repository
IAM Roles
S3 Bucket for Terraform State
Tools
Terraform
AWS
GitHub
Deliverable
terraform apply

creates the entire infrastructure.

Phase 2: Kubernetes Setup 

Install:

Jenkins
SonarQube
Prometheus
Grafana
Metrics Server
AWS Load Balancer Controller

Using:

Helm Charts
Deliverable

Access:

Jenkins
SonarQube
Grafana
Prometheus

through Load Balancer or Ingress.

Phase 3: Jenkins Production Configuration
Configure
RBAC

Create:

Admin
DevOps
Developers

roles.

Shared Libraries
vars/
src/
resources/

Reusable pipeline code.

Credentials

Store:

GitHub Token
ECR Credentials
Slack Webhook

inside Jenkins Credentials Store.

Phase 4: Build Application

Create sample application:

Option A (Recommended)

Spring Boot   note: we are going with this

Option B

NodeJS

Option C

Python Flask

Repository Structure:

app/
Dockerfile
Jenkinsfile
k8s/
terraform/
Phase 5: CI Pipeline

Pipeline Stages

Checkout
Build
Unit Test
SonarQube Scan
Trivy Scan
Docker Build
Push ECR

Example:

stage('Sonar Scan')
stage('Trivy Scan')
stage('Docker Build')
stage('Push ECR')
Phase 6: CD Pipeline

Deploy automatically to EKS.

kubectl apply -f deployment.yaml

or

helm upgrade --install
Deliverable

Every GitHub push:

GitHub
↓
Jenkins
↓
Build
↓
Security Scan
↓
ECR
↓
EKS Deployment
Phase 7: Monitoring

Install:

Prometheus
Grafana

Create dashboards:

CPU
Memory
Pod Restarts
Jenkins Health
Pipeline Metrics
Phase 8: Logging

Install:

Fluent Bit
OpenSearch

Collect logs from:

Jenkins
Application
Kubernetes
Phase 9: Notifications

Slack Integration

Notify:

Build Success
Build Failure
Deployment Success
Deployment Failure
Phase 10: Production Features
Backup

Jenkins Home

s3://jenkins-backup
Disaster Recovery

Restore Jenkins from backup.

Security
RBAC
IAM Roles for Service Accounts
Secrets Manager
Network Policies
GitHub Repositories

we will create Create separate repositories for this project:

Repository Structure
1. AWS Infrastructure

📁 aws-eks-terraform

aws-eks-terraform
├── modules
│   ├── vpc
│   ├── eks
│   ├── ecr
│   └── iam
├── environments
│   ├── dev
│   ├── uat
│   └── prod
└── README.md

Purpose:

VPC
EKS
ECR
IAM
Networking
2. Jenkins Shared Library

📁 jenkins-shared-library

jenkins-shared-library
├── vars
│   ├── build.groovy
│   ├── deploy.groovy
│   ├── trivy.groovy
│   └── sonar.groovy
├── src
└── README.md

Purpose:

Reusable Jenkins pipeline functions
Enterprise-grade Jenkins practice
3. Application Repository

📁 sample-microservice

sample-microservice
├── src
├── tests
├── Dockerfile
├── Jenkinsfile
└── README.md

I suggest using:

Spring Boot (best for enterprise)
OR
Python Flask (faster to build)

Since your goal is DevOps, Flask is sufficient.

4. Kubernetes Repository

📁 kubernetes-manifests

kubernetes-manifests
├── dev
│   ├── deployment.yaml
│   └── service.yaml
├── uat
├── prod
└── README.md

Purpose:

Deployment manifests
Environment-specific configurations
Even Better (Enterprise-Level)

Add a fifth repository:

📁 devops-observability

devops-observability
├── prometheus
├── grafana
├── alerts
├── dashboards
└── README.md

Contains:

Grafana dashboards
Prometheus rules
AlertManager configs

This shows monitoring expertise.

Final GitHub Portfolio
aws-eks-terraform
jenkins-shared-library
sample-microservice
kubernetes-manifests
devops-observability

With these 5 repositories, your GitHub profile demonstrates:

✅ Terraform
✅ AWS
✅ EKS
✅ Docker
✅ Jenkins
✅ Shared Libraries
✅ CI/CD
✅ Kubernetes
✅ Monitoring
✅ Security Scanning
✅ Production Deployments

For someone targeting DevOps/Platform Engineer roles in 2026, this is a strong portfolio project and much more impressive than a single "aws-eks-project" repository.