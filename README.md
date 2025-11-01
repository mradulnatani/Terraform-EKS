# Terraform EKS

## Overview

This repository provides a comprehensive, step-by-step guide and codebase for provisioning an Amazon Elastic Kubernetes Service (EKS) cluster using Terraform. It is designed for beginners as well as experienced users who wish to automate the setup and management of Kubernetes clusters on AWS using Infrastructure as Code (IaC) with HCL (HashiCorp Configuration Language).

---

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Project Structure](#project-structure)
3. [Configuration](#configuration)
4. [Deployment Steps](#deployment-steps)
5. [Validation](#validation)
6. [Useful Commands](#useful-commands)
7. [Cleanup](#cleanup)
8. [Support](#support)
9. [References](#references)

---

## Prerequisites

Before you begin, ensure you have the following:

- **AWS Account** with sufficient permissions to create EKS resources.
- **Terraform** installed on your machine ([Install Terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli)).
- **AWS CLI** installed and configured ([Configure AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html)).
- **kubectl** for interacting with your cluster ([Install kubectl](https://kubernetes.io/docs/tasks/tools/)).
- Basic understanding of cloud resources and Kubernetes.

---

## Project Structure

The repository is organized as follows:

```
.
├── main.tf           # Core Terraform configuration
├── variables.tf      # Input variables definitions
├── outputs.tf        # Output values after deployment
├── providers.tf      # AWS provider configuration
├── versions.tf       # Terraform and provider version constraints
├── modules/          # (Optional) Reusable modules (VPC, EKS, etc.)
└── README.md         # This tutorial and documentation
```

---

## Configuration

1. **Clone the repository:**

   ```bash
   git clone https://github.com/mradulnatani/Terraform-EKS.git
   cd Terraform-EKS
   ```

2. **Configure your AWS credentials:**

   Ensure your AWS CLI is authenticated:
   ```bash
   aws configure
   ```

3. **Customize input variables:**

   Edit `variables.tf` to set values for your desired region, cluster name, node group settings, and networking details.

---

## Deployment Steps

### 1. Initialize Terraform

```bash
terraform init
```
This command downloads necessary provider plugins and prepares the working directory.

### 2. Review the Execution Plan

```bash
terraform plan
```
This step displays the actions Terraform will perform. Review the output to ensure resources will be created as expected.

### 3. Apply the Configuration

```bash
terraform apply
```
You will be prompted to confirm. Type `yes` to proceed. Terraform will now provision your EKS cluster and related resources.

---

## Validation

Once deployment is complete:

1. **Update your kubeconfig:**

   ```bash
   aws eks --region <your-region> update-kubeconfig --name <your-cluster-name>
   ```

2. **Test cluster access:**

   ```bash
   kubectl get nodes
   ```
   You should see your EKS worker nodes listed.

---

## Useful Commands

- **Scale Node Group:**
  ```bash
  kubectl scale nodegroup <nodegroup-name> --replicas=<count>
  ```

- **Destroy Infrastructure:**

  ```bash
  terraform destroy
  ```
  This command will remove all resources created by Terraform.

---

## Cleanup

After testing, you can clean up all resources to avoid unnecessary charges:

```bash
terraform destroy
```
Confirm when prompted to ensure all AWS resources are deleted.

---

## Support

For issues or questions, please open an issue in the [GitHub Issues](https://github.com/mradulnatani/Terraform-EKS/issues) section.

---

## References

- [Terraform AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)
- [AWS EKS Documentation](https://docs.aws.amazon.com/eks/latest/userguide/getting-started.html)
- [Terraform Modules](https://www.terraform.io/language/modules)

---

**By following this tutorial, you will have a reproducible, automated workflow for deploying Kubernetes clusters on AWS using Terraform. Happy automating!**
