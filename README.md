#🛠 E-RequestControl Infrastructure as Code (IaC)

Terraform-based infrastructure management for E-RequestControl application deployed on AWS EKS.

##🏗 Architecture Overview

This repository contains Terraform configurations to provision and manage the complete infrastructure for the E-RequestControl system on AWS, including EKS cluster, networking, security groups, and related resources.

##📊 Provisioning Workflow 

```mermaid
graph TD
    A[Terraform Code Changes<br/>locally or in IDE] --> B[Push to stage branch<br/>changes in /terraform]
    B --> C{Success?}
    C -->|Yes| D[Run Terraform Plan<br/>terraform plan]
    C -->|No| E[Job Stopped]
    D --> F{terraform plan Success?}
    F -->|Yes| G[Wait for Merge Request to main]
    F -->|No| E
    G --> H[Merge to main branch]
    H --> I[Push to main branch<br/>Run Terraform Apply<br/>terraform apply]
    I --> J[Configure AWS Credentials]
    J --> K[Get kubeconfig for EKS]
    K --> L[Install Ingress Controller]
    L --> M[Infrastructure Ready]
```
