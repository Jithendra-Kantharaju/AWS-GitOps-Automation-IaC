
# GitOps IaC Pipeline for Kubernetes on AWS

This repository contains the Infrastructure as Code (IaC) for provisioning a complete EKS (Elastic Kubernetes Service) cluster on AWS using Terraform. It is the foundational part of a two-repository GitOps project.

**Application Repository:** [AWS-Gitps-Automation-Actions

## 📐 Project Architecture
This project uses a dual-repository approach to separate infrastructure from application concerns, both automated via GitHub Actions.
<div align="center">
  <img src="https://github.com/user-attachments/assets/cde9d26b-8508-46cb-9375-52b7f33692d7" width="600px" alt="GitOps Automation">
</div>

## 🏛️ Infrastructure Workflow (`terraform.yml`)
The GitHub Actions workflow automates validation and deployment of AWS infrastructure using a Git-flow strategy.

### `stage` Branch
- Trigger: Push to `stage` or PR to `main`
- Actions:
  - Checkout Code
  - Setup Terraform (v1.6.3)
  - Terraform Init (S3 backend)
  - Validate & Format
  - Plan (saved as artifact)

### `main` Branch
- Trigger: Push to `main`
- Actions:
  - Repeat planning steps
  - Apply changes
  - Install Nginx Ingress Controller

## 🛠️ Tools Used
- GitHub Actions
- Terraform
- AWS (EKS, VPC, S3)
- Kubernetes
- Nginx

## 🚀 Getting Started
1. Fork this repository.
2. Configure GitHub Secrets:
   - `AWS_ACCESS_KEY_ID`
   - `AWS_SECRET_ACCESS_KEY`
   - `BUCKET_TF_STATE`
3. Push changes to `terraform` directory on `stage` branch.
