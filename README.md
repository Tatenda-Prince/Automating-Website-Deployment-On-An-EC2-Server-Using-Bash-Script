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


![image alt](https://github.com/Tatenda-Prince/Automating-Website-Deployment-On-An-EC2-Server-Using-Bash-Script/blob/5ff8c540b20a16518969953fe97ec39235c52c3d/Images/Screenshot%202024-12-23%20110925.png)


Continue to the Network settings —

Each custom AWS account network is automatically preconfigured with a default VPC when an EC2 Instance in launched. Also, we will keep “Auto-assign public IP” enabled, as this allows our EC2 Instance to automatically receive a public IP address to enable it to connect to the internet upon launch.

We will leave these setting in the default state, as seen below.

Continue to the Firewall (Security Group) settings —

As stated below, Security Groups serve as a set of Firewall rules that you can use to control traffic to your instance. We are going to allow “SSH” traffic to enable us to securely connect to our EC2 Instance and also “HTTPS” and “HTTP” so we can send requests and be served our Webpage in our browser over the internet.


![image alt](https://github.com/Tatenda-Prince/Automating-Website-Deployment-On-An-EC2-Server-Using-Bash-Script/blob/5d6c0e0be09ed085ef0f07e4127c94a1b2fc2ef8/Images/Screenshot%202024-12-23%20111021.png)


Continue to the Summary —

Make sure all configurations align with our previous steps, then click “Launch instance”, as seen below.


![image alt](https://github.com/Tatenda-Prince/Automating-Website-Deployment-On-An-EC2-Server-Using-Bash-Script/blob/3e0dfedd8225d3b002a6571ad797287c5bdb4620/Images/Screenshot%202024-12-23%20111044.png)



Success!
You’ve just launched your first Amazon EC2 Instance on AWS. Now we can proceed to Step 2 — SSH into the EC2 Instance.


# Step 2: SSH into Amazon EC2 Instance

Verify EC2 is running and navigate to options to connect to instance

Navigate to your EC2 Instances and verify that the new EC2 Instance we just launched is running.

Once we’ve verified our EC2 Instance is running, navigate to the top right pane, click “Actions” and select “Connect” as seen below.


![image alt](https://github.com/Tatenda-Prince/Automating-Website-Deployment-On-An-EC2-Server-Using-Bash-Script/blob/7698932cdadf80fd0d88c922021d6bff2321ea6f/Images/Screenshot%202024-12-23%20111154.png)


Click on the “SSH Client tab”, as show below. AWS is helpful enough to suggest some instructions on how we connect to the EC2 Instance, however, I will walk you through the whole process.


![image alt](https://github.com/Tatenda-Prince/Automating-Website-Deployment-On-An-EC2-Server-Using-Bash-Script/blob/f29a6a7f466de1d546947b16e646f3b8d2195a40/Images/Screenshot%202024-12-23%20111248.png)


Use Key pair to ssh into EC2 Instance from CLI on local system
Locate the directory path where the downloaded key pair is stored and run the following command to change into that working directory —

cd [key_pair_file_directory_path]


To prevent others who may access your system from having unauthorized access to the key pair file, we need to modify the permissions of the file so only the user can read it.

Modify the permissions and verify the modifications were made by running the following two separate commands respectively —



chmod 400 [key_pair_file_name]


ls -al

Run ssh command passing in key pair file to authenticate into the EC2 Instance
We need to run the ssh command in your CLI and in addition, add the “-i” option to pass the key pair file at the same time to authenticate into your EC2 Instance.

You can find your EC2 Instance Public IPv4 address by navigating to the EC2 Instance dashboard and copying the “Pubic IPv4 address”, as seen below.

Run the command below to ssh into the EC2 with the key pair file —

ssh -i "[key_pair_name.pem]" ec2-user@[EC2_Public_IPv4_Address].compute-1.amazonaws.com

Success!
If you did all the steps correctly, you should have similar results as seen below and now you have connected into your EC2 Instance!


![image alt](https://github.com/Tatenda-Prince/Automating-Website-Deployment-On-An-EC2-Server-Using-Bash-Script/blob/d5c6ecbecf06407c15579f2ec98c1148dc867d47/Images/Screenshot%202024-12-23%20112115.png)


# Step 3: Create Bash Script to automate Website deployment

Create new script directory and use vim to create and edit script file

mkdir Scripts


cd Scripts


Use Vim or the Nano to create and edit a new script file with the following command —


sudo chmod u+x [script_name.sh]


./[scipt_name.sh]

![image alt](https://github.com/Tatenda-Prince/Automating-Website-Deployment-On-An-EC2-Server-Using-Bash-Script/blob/20e4cf0757417f7579dfd0118794ac5e878c07d0/Images/Screenshot%202024-12-23%20115608.png)


The bash script above  updates all yum package repositories then installs an Apache Web Server to serve content to our browsers. The server is then started and then enabled. The last line adds html code to an “index.html” file which enables our Server to serve our custom Website through our EC2 Instance.


# Step 4: View custom Webpage served by Apache Web Server, powered on EC2.

Open your desired browser and paste the public IPv4 address of your Amazon EC2 Instance in the address bar, then hit “enter” on your keyboard.

You should see your custom Website, as seen below!


![image alt](https://github.com/Tatenda-Prince/Automating-Website-Deployment-On-An-EC2-Server-Using-Bash-Script/blob/0c334c4d5aab715cf4680d186cab9495cae1a43a/Images/Screenshot%202024-12-23%20115626.png)

# YAY Congratulations!

You’ve automated the deployment of a Website using an Apache Web Server on an Amazon EC2 Instance.








