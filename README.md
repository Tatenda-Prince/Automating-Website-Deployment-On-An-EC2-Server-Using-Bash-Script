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


![image alt](https://github.com/Tatenda-Prince/Automating-Website-Deployment-On-An-EC2-Server-Using-Bash-Script/blob/c2abe1c466450931f0870d7892b468b4413c09bc/Images/Screenshot%202024-12-23%20110601.png)

You should now see your Amazon EC2 configuration options page. Note, most of the configurations will remain at their default state to launch our required EC2 Instance.

Configure and Launch EC2

The first field allows you to name your EC2 Instance. We also have the option to add tags. Tags act as a label which can be used to group resources in AWS, but for now, we will not add any.

Continue to select the desired Amazon AMI —

We will choose the “Amazon Linux 2 AMI” of the latest 5.10 Kernel with a 64-bit (x86) architecture, as seen below.

![image alt](https://github.com/Tatenda-Prince/Automating-Website-Deployment-On-An-EC2-Server-Using-Bash-Script/blob/3daba989e62dddffc6a636aa3917556ad8ba99e8/Images/Screenshot%202024-12-23%20110706.png)

Proceed to the Instance Type options —

We will choose the “t2.micro” which is part of the AWS free tier. This instance type offers 750 hours free use of Linux and Windows instances each month for one year for new AWS customers.

![image alt](https://github.com/Tatenda-Prince/Automating-Website-Deployment-On-An-EC2-Server-Using-Bash-Script/blob/9c2145b50565055bcc109215d4775f39356b3028/Images/Screenshot%202024-12-23%20110727.png)

Proceed to the Key pair option —

Click on the “Create new key pair” to create a new key pair, then enter your desired key pair name. Select “RSA” for key pair type and “.pem” for private key file format.

Click on “Create key pair”, as show below. The “.pm” file should automatically start downloading on your local system. Locate the file after the download is complete and store it in a safe directory. Later, we will use this key pair to connect to our EC2 Instance through ssh.

![image alt]()

Continue to the Network settings —

Each custom AWS account network is automatically preconfigured with a default VPC when an EC2 Instance in launched. Also, we will keep “Auto-assign public IP” enabled, as this allows our EC2 Instance to automatically receive a public IP address to enable it to connect to the internet upon launch.

We will leave these setting in the default state, as seen below.

![image alt]()

Continue to the Firewall (Security Group) settings —

As stated below, Security Groups serve as a set of Firewall rules that you can use to control traffic to your instance. We are going to allow “SSH” traffic to enable us to securely connect to our EC2 Instance and also “HTTPS” and “HTTP” so we can send requests and be served our Webpage in our browser over the internet.

![image alt]()

Continue to the Summary —

Make sure all configurations align with our previous steps, then click “Launch instance”, as seen below.

![image alt]()




