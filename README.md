# Terraform Automated AWS Web Infrastructure

This project builds a complete AWS web infrastructure using Terraform. It’s designed to show how you can provision cloud resources in a predictable, repeatable way and automate everything from networking to load-balanced web servers.

---
# Architecture of Terraform Automated AWS Web Infrastructure
![AWS Terraform Infra](https://github.com/user-attachments/assets/7462b8e6-4ebb-43e2-a75f-403105b31da0)


## Overview

The setup includes a VPC, public subnets across two Availability Zones, an Internet Gateway, route tables, security groups, EC2 instances, and an Application Load Balancer. Two Ubuntu servers run Apache with custom welcome pages and are registered with a target group behind the ALB.

The entire environment can be created and destroyed through Terraform in a few commands, making it ideal for learning, demonstrations, or portfolio projects.

---

## Architecture Highlights

### **VPC**

A dedicated virtual network that isolates all project resources.

### **Subnets**

Two public subnets placed across two AZs for better availability.

### **Internet Gateway & Route Tables**

Provide internet access to instances inside public subnets.

### **Security Groups**

Separate groups for EC2 and ALB. Each group follows the principle of least privilege.

### **EC2 Instances**

Two Ubuntu servers with Apache installed through user data. Each displays a different welcome message.

### **Application Load Balancer**

Splits incoming traffic between the two EC2 instances. A listener on port 80 forwards traffic to a target group.

### **S3 Bucket**

Pre-created for future use, such as serving static content or storing logs.

---

 ## Cloud Infrastructure:
 ## VPC Design:
 Creating and configuring a custom Virtual Private Cloud.
Subnetting across multiple Availability Zones: Designing a network layout for high availability and fault tolerance.
Internet Gateway and route configuration: Enabling internet connectivity for public resources.
Security Groups following least-privilege rules: Implementing network-level security.
## Compute and Web Hosting:
EC2 provisioning with Terraform: Automating the launch of virtual servers.
Apache installation through user data: Using bootstrap scripts for software setup.
Load balanced web servers with health checks: Ensuring application availability and traffic distribution.
## Storage:
S3 bucket creation for static content and future use cases: Understanding object storage for various purposes.
## Infrastructure as Code (IaC):
AWS infrastructure managed using Terraform: Applying IaC principles to cloud deployments.
Use of providers, resources, variables, and outputs: Mastering the core components of Terraform.
Dependency handling and remote state management: Understanding how Terraform manages resource creation order and state (though remote state setup is a future enhancement for this project).
Environment cleanup using terraform destroy: Efficiently tearing down infrastructure.
## Automation:
Automated provisioning of network, compute, and load balancing: Deploying complex environments with a single command.
Reproducible deployments: Ensuring consistent environments every time.

## Prerequisites

Before running this project, make sure you have:

* An AWS account
* AWS CLI configured with an IAM user
* Terraform installed
* VS Code (optional but recommended)

To verify your AWS setup:

```bash
aws configure
```

---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/terraform-aws-project.git
cd terraform-aws-project
```

### 2. Initialize Terraform

```bash
terraform init
```

### 3. Review Changes

```bash
terraform plan
```

### 4. Deploy Infrastructure

```bash
terraform apply
```

To skip the confirmation prompt:

```bash
terraform apply --auto-approve
```

### 5. Access Your Application

Once the deployment completes, Terraform will output the ALB DNS name.
Paste it into your browser to see your web pages served from the two EC2 instances.

---

## Project Structure

| File                        | Description                                                                          |
| --------------------------- | ------------------------------------------------------------------------------------ |
| **main.tf**                 | All core AWS resources (VPC, subnets, IGW, route tables, ALB, EC2, security groups). |
| **variables.tf**            | Configurable values such as CIDR blocks.                                             |
| **outputs.tf**              | Displays important values like the ALB DNS name.                                     |
| **user-data-abhishek.sh**   | User data script for instance 1.                                                     |
| **user-data-cloudchamp.sh** | User data script for instance 2.                                                     |

---

## Cleanup

To avoid unexpected AWS charges, destroy all resources when you're done:

```bash
terraform destroy
```

Or:

```bash
terraform destroy --auto-approve
```

---

## Troubleshooting Guide

Here are common issues and quick ways to fix them:

* **Syntax errors**
  Run `terraform validate` after each change.

* **Permission issues**
  Make sure your IAM user has the correct permissions.

* **Unhealthy targets in ALB**
  Check Apache is running and verify the user data script.

* **User data not executing**
  Inspect `/var/log/cloud-init-output.log` on the EC2 instance.

---



It’s a strong project for cloud and DevOps roles and easy to discuss in interviews.

---

If you want, I can also help you improve the code structure, add modules, or write a short LinkedIn post describing this project.
