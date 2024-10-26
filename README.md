Project Setup: "Exam Work" at IT Step
Welcome! This guide provides instructions for setting up my "Exam Work" project on AWS.

Overview
This project uses the following AWS services:

EC2
ELB
ELK
EKS
Grafana Stack
RDS
Route 53 with DNSSEC
Jenkins
Ansible
Step 1: Environment Setup
Use Visual Studio Code with the following plugins installed:
AWS
Kubernetes
Terraform
Ensure that the AWS CLI is installed on your system.
Configure the AWS CLI by running:
bash
Копіювати код
aws configure
Step 2: IAM User Setup in AWS
Create or use an existing IAM user with access to:
EC2
S3
ELB
EKS
Assign the custom permissions provided in the file named "custom permissions".
