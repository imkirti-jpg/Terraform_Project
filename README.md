# Setting up AWS Infrastructure using Terraform

## Project Overview
This Terraform project automates the deployment of a highly available web infrastructure on AWS. It creates a complete environment including VPC, subnets, security groups, EC2 instances, and an Application Load Balancer. The solution is designed for 99.9% availability across multiple availability zones.


**Components:**
- **VPC**: 10.0.0.0/16 network
- **Public Subnets**: 10.0.0.0/24 (us-east-1a), 10.0.1.0/24 (us-east-1b)
- **EC2 Instances**: t2.micro with Apache web servers
- **Application Load Balancer**: Distributes traffic across instances
- **Security Group**: Allows HTTP (80) and SSH (22) access
- **S3 Integration**: For static asset storage (commented out)

## Features
- 🚀 **Multi-AZ Deployment**: Instances in separate availability zones
- ⚖️ **Load Balancing**: ALB with health checks and target groups
- 🔒 **Security**: Configurable security groups and network isolation
- 🔄 **Automated Provisioning**: User data scripts for instance initialization
- 📊 **Monitoring Ready**: Integration with CloudWatch metrics
- 💾 **Storage Options**: S3 bucket for static assets
- 📦 **Infrastructure as Code**: Fully version-controlled environment



## Prerequisites
- **AWS Account** with IAM permissions:
  - AmazonEC2FullAccess
  - AmazonVPCFullAccess
  - AmazonS3FullAccess
  - IAMReadOnlyAccess
- **Terraform** v1.0+ ([Installation Guide](https://learn.hashicorp.com/tutorials/terraform/install-cli))
- **AWS CLI** v2.0+ ([Installation Guide](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html))
- **Git** for version control
- **SSH Key Pair** in AWS region us-east-1

## Deployment Guide 

### 1. Repository Setup
```bash
git clone https://github.com/yourusername/terraform-aws-web-infra.git
cd terraform-aws-web-infra
```

### 2. AWS Configuration
Configure your AWS credentials:
```bash
aws configure
# Follow prompts to enter AWS Access Key, Secret Key, and default region
```

### 3. Terraform Initialization
```bash
terraform init
```
This will:
- Initialize backend
- Install AWS provider plugins
- Create .terraform directory

### 4. Infrastructure Planning
```bash
terraform plan 
```
Review the execution plan to verify resource creation

### 5. Infrastructure Deployment
```bash
terraform apply
```
Confirm with `yes` when prompted

### 6. Verification
After deployment completes:
1. Access ALB DNS name from outputs
2. Verify both instances are serving traffic


### Infrastructure Cleanup
```bash
terraform destroy
```
**Note:** This will permanently delete all resources. S3 buckets must be empty before destruction.

---
**Maintained by**: Kirti singh
**Last Updated**: june 22, 2025
**Terraform Version**: v1.5.7  
**AWS Provider Version**: v5.11.0





