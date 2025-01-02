# Deployment of Microservices — Sample Voting Application on Kubernetes (EKS)

## Deployment of Microservices-Sample voting application on EKS
This project focuses on deploying a Sample Voting Application on Amazon Elastic Kubernetes Service (EKS). By utilizing Kubernetes as our container orchestration platform, we’ll explore how microservices can be efficiently managed, scaled, and maintained in a production-grade cloud environment.

Join us as we navigate through the deployment of a distributed application composed of five microservices, leveraging Kubernetes’ powerful features like automated scaling, self-healing, and seamless integration with AWS. Let’s unlock the potential of microservices in the cloud together!
### Project Reference Architectural Diagram
![Architecture diagram](https://github.com/taofeeklanre/voting-app/blob/main/Simple%20Voting%20App.gif)

## Project Overview
Deploying a dynamic website on AWS involves setting up and managing various infrastructure resources such as VPCs, subnets, security groups, EC2 instances, load balancers, and more. Manually provisioning these resources can be time-consuming, error-prone, and repetitive, especially when scaling or deploying multiple applications.

This project leverages Terraform Modules to automate the provisioning of AWS infrastructure, combined with Docker, Amazon ECR, and ECS to deploy and manage a dynamic web application. By defining your infrastructure as code (IaC), you achieve:

1. Efficiency: Rapidly provision and manage infrastructure.
2. Consistency: Ensure uniform configurations across environments.
3. Scalability: Easily scale resources to meet demand.
4. Maintainability: Simplify updates and modifications through reusable modules.

## Introduction
### Why Automation?
As a DevOps engineer, managing infrastructure manually across multiple servers can be daunting. For instance, configuring 100 servers individually to host web applications is not only time-consuming but also increases the risk of human errors. Automation addresses these challenges by:

1. Enhancing Efficiency: Automate repetitive tasks to save time.
2. Ensuring Consistency: Maintain uniform configurations across all servers.
3. Improving Reliability: Reduce the likelihood of errors, leading to more stable deployments.
4. Scaling Operations: Easily manage and scale infrastructure as your needs grow.

### Why Terraform and Terraform Modules?
Terraform is an open-source IaC tool that allows you to define and provision infrastructure using configuration files. Its key features include:

1. Declarative Syntax: Define the desired state of your infrastructure, and Terraform handles the provisioning.
2. Version Control: Manage infrastructure configurations using version control systems like Git.
3. Multi-Cloud Support: Manage resources across various cloud providers, including AWS, Azure, and Google Cloud.
4. Terraform Modules: Encapsulate and reuse infrastructure code, promoting modularity and maintainability.
5. Terraform Modules are collections of Terraform files that are grouped together to perform a specific function. They enable you to abstract complex configurations into reusable components, making your code more organized and easier to manage.

### Objectives
Building on the fundamentals of AWS infrastructure management, this project aims to:

1. Automate Infrastructure Provisioning: Use Terraform Modules to define and deploy AWS resources.
2. Deploy a Dynamic Web Application: Utilize Docker, Amazon ECR, and ECS to deploy and manage a scalable web application.
3. Achieve Scalability and Reliability: Ensure the deployed application can scale based on demand and maintain high availability.
4. Enhance Maintainability: Use reusable Terraform Modules for organized and maintainable infrastructure code.

By the end of this project, you will have a comprehensive understanding of deploying a dynamic web application on AWS using Terraform, Docker, Amazon ECR, and ECS.

Prerequisites
Before you begin, ensure you have the following tools and accounts set up:

a. GitHub Account

#### Why GitHub?
1. Version Control: Host your code and track changes efficiently.
2. Collaboration: Easily collaborate with others by sharing repositories.
3. Issue Tracking: Manage tasks, bugs, and feature requests seamlessly.

b. Setup:
Sign up for a free GitHub account.

c. Visual Studio Code

### Why Visual Studio Code?
1. Integrated Development Environment: Write and edit Terraform configurations and other code with ease.
2. Built-in Git Integration: Manage version control directly within the editor.
3. Extensibility: Enhance functionality with a vast library of extensions.
Setup:
Download and install Visual Studio Code.

d. AWS Account

Ensure you have access to AWS services required for this project.
Setup:
Sign up for an AWS account.

e. SSH Key Pairs

Generate SSH key pairs for secure access to your AWS instances.
Setup:
Use ssh-keygen to generate key pairs.

f. Terraform Installed on Your Machine

### Why Terraform?
Define and provision AWS infrastructure as code.
Setup:
Follow the Terraform installation guide.



Step-by-Step Guide
Follow the steps below to set up and deploy your dynamic web application on AWS using Terraform Modules, Docker, Amazon ECR, and ECS.

1. ### Install and Set Up Terraform
Objective: Install Terraform on your local machine to define and provision AWS infrastructure.

Actions:

Download Terraform from the official website.

Follow the installation instructions for your operating system.

Verify the installation by running:

"terraform version"

2. ### Create a GitHub Account
Objective: Set up a GitHub account to host your Terraform configurations and application code.

Actions:

Visit GitHub and sign up for a free account.

Verify your email address and complete the account setup.

3. ###  Install Git on Your Laptop
Objective: Install Git to manage version control for your project.

Actions:

Download Git from the official website.

Follow the installation instructions for your operating system.

Configure Git with your GitHub credentials:

git config --global user.name "Your Name"
git config --global user.email "taolanre99@gmail.com"

4. ### Generate Keypairs for Secure Connections
Objective: Create SSH key pairs for secure access to your AWS instances and GitHub repositories.

Actions:

Generate an SSH key pair using the following command:

ssh-keygen -t rsa -b 4096 -C "taolanre99@gmail.com"

Follow the prompts to save the key pair to the default location.

5. ### Add the Public SSH Key to GitHub
Objective: Enable secure interactions with your GitHub repositories using SSH.

Actions:

Copy the contents of your public SSH key:

cat ~/.ssh/id_rsa.pub

Navigate to GitHub > Settings > SSH and GPG keys > New SSH key.

Paste the copied key and save.

6. ### Install Visual Studio Code
Objective: Set up a powerful code editor for writing Terraform configurations and managing your project.

Actions:

Download Visual Studio Code from the official website.

Follow the installation instructions for your operating system.

Install relevant extensions for Terraform and Git.

7. ###  Install AWS Command Line Interface (CLI)
Objective: Facilitate interaction with AWS services directly from your terminal.

Actions:

Follow the AWS CLI installation guide for your operating system.

Verify the installation by running:

aws --version

8. ###  Create an IAM User in AWS
Objective: Set up a dedicated IAM user with appropriate permissions for managing AWS resources.

Actions:

Log in to the AWS Management Console.

Navigate to IAM > Users > Add user.

Enter a username and select Programmatic access.

Attach the necessary policies (e.g., AdministratorAccess for simplicity, but consider least privilege for production).

Complete the user creation and securely store the access key and secret access key.

9. ###  Create Access Keys for IAM User
Objective: Generate access keys for programmatic access to AWS services.

Actions:

In the IAM console, select the user you created.

Navigate to Security credentials > Create access key.

Download the access key file and store it securely.

10. ### Run the AWS Configure Command for Easy Setup
Objective: Configure the AWS CLI with your IAM user's credentials and default settings.

Actions:

Run the following command:

aws configure

Enter your Access Key ID, Secret Access Key, Default region name (e.g., us-east-1), and Default output format (e.g., json).

After completing the installation and setup steps, you are ready to deploy your dynamic web application on AWS using Terraform, Docker, Amazon ECR, and ECS. The high-level steps include:

11. ### Define Infrastructure with Terraform Modules:

Use reusable Terraform modules to define AWS resources such as VPCs, subnets, security groups, EC2 instances, ECR repositories, and ECS clusters.
Initialize and Apply Terraform Configuration:

Initialize Terraform in your project directory:

terraform init

Review the planned changes:

terraform plan

Apply the configuration to provision resources:

terraform apply

Build and Push Docker Images:

Create a Dockerfile for your web application.
Build the Docker image:

docker build -t your-app-image .

Authenticate Docker to Amazon ECR:

aws ecr get-login-password --region your-region | docker login --username AWS --password-stdin your-account-id.dkr.ecr.your-region.amazonaws.com

Tag and push the image to ECR:

docker tag your-app-image:latest your-account-id.dkr.ecr.your-region.amazonaws.com/your-repo:latest

docker push your-account-id.dkr.ecr.your-region.amazonaws.com/your-repo:latest

Deploy to ECS:

Update your ECS task definition to use the Docker image from ECR.

Deploy the task definition to your ECS cluster.

Verify that your application is running and accessible via the Application Load Balancer.

Access Your Web Application:
### Website displayed
![Architecture diagram](https://github.com/taofeeklanre/terraform-module-project-code/blob/main/website-1.jpg?raw=true)
Navigate to your registered domain name (e.g., www.zabinets.com) in my own case to access the deployed web application.

Cleanup
To avoid incurring unnecessary AWS charges, follow these cleanup steps after completing the project:

Destroy Terraform-Managed Infrastructure:

Navigate to your Terraform project directory.
Run the following command to destroy all resources:

terraform destroy

Delete ECR Repositories:

Remove Docker images and ECR repositories from the AWS Management Console.
Terminate EC2 Instances:

Ensure all EC2 instances launched for the Bastion Host, Ansible Server, and Web Servers are terminated.
Delete S3 Buckets:

Remove any S3 buckets used for storing environment files or other assets.
Remove Load Balancers and SSL Certificates:

Delete the Application Load Balancer and associated SSL certificates from AWS Certificate Manager.
Delete Route 53 Domain and Records:

If no longer needed, delete your domain registration and DNS records in Route 53.
Remove IAM Users and Access Keys:

Delete IAM users and associated access keys if they are no longer required.
Delete GitHub Repositories:

Remove the GitHub repository if it’s no longer needed or keep it for future reference.
Contributing
Contributions are welcome! If you find any issues or have suggestions for improvements, please open an issue or submit a pull request.

How to Contribute
Fork the Repository

Click the "Fork" button at the top right of this repository's page on GitHub.
Create a New Branch

git checkout -b feature/YourFeature
Commit Your Changes

git commit -m 'Add some feature'
Push to the Branch

git push origin feature/YourFeature
Open a Pull Request

Navigate to the original repository and open a pull request from your forked repository.

### Contact
For any questions or inquiries, please contact:

Taofeek Agboola

Email: taolanre99@gmail.com

GitHub: [My-Github-username](https://github.com/taofeeklanre)

LinkedIn:[My-LindkedIn-User]( inkedin.com/in/taofeek-agboola)

Happy deploying! 🚀
