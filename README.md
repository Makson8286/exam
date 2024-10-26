# Project Setup: "Exam Work" at IT Step

Welcome! This guide provides instructions for setting up my "Exam Work" project on AWS.

### Overview
This project uses the following AWS services:
- **EC2**
- **ELB**
- **ELK**
- **EKS**
- **Grafana Stack**
- **RDS**
- **Route 53 with DNSSEC**
- **Jenkins**
- **Ansible**

### Step 1: Environment Setup
1. Use **Visual Studio Code** with the following plugins installed:
   - **AWS**
   - **Kubernetes**
   - **Terraform**
2. Ensure that the **AWS CLI** is installed on your system.
3. Configure the AWS CLI by running the following command:
   ```bash
   aws configure
   ```

### Step 2: IAM User Setup in AWS
1. Create or use an existing IAM user with access to:
   - **EC2**
   - **S3**
   - **ELB**
   - **EKS**
2. Assign the custom permissions provided in the file named **"custom permissions."**
