# Automating-Website-Deployment-On-An-EC2-Server-Using-Bash-Script
Creating a custom website on EC2 server using bash script.

![image alt](https://github.com/Tatenda-Prince/Automating-Website-Deployment-On-An-EC2-Server-Using-Bash-Script/blob/1a6000875161c4895ae00b5747a8a06abff6ceec/Images/Screenshot%202024-12-23%20121404.png)

# Intro 

Together, I will guide you through how we can automate the deployment of a Website, served by an Apache Web Server on an Amazon EC2 Instance that runs Amazon Linux 2. We will be using the AWS Management Console along with a preferred Command Line Interface on your local system.

# Background

# Amazon Web Services (AWS)

An Amazon EC2 Instance is basically an AWS branded virtual machine that offers computing services on AWS. Using Amazon EC2 Instances, eliminates our need to invest in hardware up front, giving us the opportunity to develop and deploy applications exponentially faster and at lower costs.

# AMI (Amazon Machine Image)

An AMI is a prepackaged system state, referred to an image, that provides the critical operation system information required for the launch of an Amazon EC2 Instances.

# Amazon EC2 (Elastic Compute Cloud) Instance Type

Amazon EC2 offers a wide range of instance types which are optimized for different use cases that require varying capacity combinations of CPU, memory, storage and networking.

# Key Pair

A Key Pair is a combination of a public key that is used to encrypt data and a private key that is used to decrypt data. It can also be used to provide authentication into systems.

# Virtual Private Cloud (VPC)

Virtual Private Cloud is a service on AWS that offers a virtual private network logically isolated from other virtual networks on the platform. You can specify network configurations including IP address range, subnets, gateways and security groups.

# Use Case 

You are a Cloud Engineer for UP THE CHELS TECH tasked with creating an Amazon EC2 Instance on AWS to host the organizations new website. Traditionally, UP THE CHELS TECH hosts their websites on premise which involves purchasing very expensive infrastructure in a data center. The organization now wants to migrate to the cloud to decrease costs of capital expenditure and increase efficiency.

# Prerequisites

AWS Account with an IAM User

IAM Permissions following best practices

Access to Command Line Interface on local system

Knowledge of Vim

# Step 1: Configure and Launch Amazon EC2 Instance

Navigate to EC2 configuration page

Before we can configure the Amazon EC2 Instance, we need to first sign into your AWS IAM Account. After signing into your AWS account, navigate to the top of dashboard to search for the EC2 Service, click on “EC2”, then “Launch instance”, as seen below.

![image alt](https://github.com/Tatenda-Prince/Automating-Website-Deployment-On-An-EC2-Server-Using-Bash-Script/blob/a35323baf56102c1eda7471c458d66568461d9b4/Images/Screenshot%202024-12-23%20110527.png)

![image alt]()


