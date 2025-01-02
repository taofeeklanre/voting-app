# Deployment of Microservices — Sample Voting Application on Kubernetes (EKS)

## Deployment of Microservices-Sample voting application on EKS
This project focuses on deploying a Sample Voting Application on Amazon Elastic Kubernetes Service (EKS). By utilizing Kubernetes as our container orchestration platform, we’ll explore how microservices can be efficiently managed, scaled, and maintained in a production-grade cloud environment.

Join us as we navigate through the deployment of a distributed application composed of five microservices, leveraging Kubernetes’ powerful features like automated scaling, self-healing, and seamless integration with AWS. Let’s unlock the potential of microservices in the cloud together!
### Project Reference Architectural Diagram
![Architecture diagram](https://github.com/taofeeklanre/voting-app/blob/main/Simple%20Voting%20App.gif)

##  Microservices Overview
![Architecture diagram](https://github.com/taofeeklanre/voting-app/blob/main/diagram-export-10-26-2024-8_04_03-PM.png)
The sample voting application is made up of the following microservices:

Voting-App (Python): A frontend service that allows users to vote between Cats and Dogs.
VotingResult-App (Node.js): A frontend service displaying real-time voting results.
Worker-App (.NET): A backend service responsible for processing and storing votes.
Redis: Used as an in-memory cache for fast access to vote data.
Each service is containerized using Docker, and Kubernetes is used for orchestration. The project demonstrates the power of containerized microservices and how to deploy them effectively on AWS using EKS.

## Objective
The main goal of this project is to:

Deploy a containerized sample voting application using Amazon EKS.
Demonstrate the use of Kubernetes for orchestration, scaling, and management of microservices.
Implement best practices for setting up a cloud-native microservices architecture.
Show how to use AWS services such as EC2, IAM, EKS, and eksctl for seamless application deployment.

### Pre-requisite

Before starting the deployment process, ensure you have the following tools installed:

a. Install AWS CLI
The AWS CLI is used for managing AWS services directly from the command line. To install the AWS CLI, follow the instructions in the [Official documentation](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).

b. Install Kubectl
Kubectl is a command-line tool used to interact with your Kubernetes clusters. You can install kubectl by following the instructions [here](https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html#windows_kubectl).

c. Install Eksctl
Eksctl is a simple CLI tool for creating and managing clusters on Amazon EKS. To install eksctl, follow the steps in the [Official documentation](https://eksctl.io/installation/).

# Step-by-Step Guide to the Project
1. ## Setup IAM User Permissions Required for eksctl to Work
Ensure that the IAM user or role used for this project has the necessary permissions for creating and managing EKS clusters. You’ll need permissions to create resources like EC2 instances, IAM roles, and VPCs. A sample IAM policy can be found [here](https://eksctl.io/installation/).
![Architecture diagram](https://github.com/taofeeklanre/voting-app/blob/main/1_ZjIqS7c7vVUbAJNKafsJHQ.jpeg)


2. ## Create the GitHub Repository for Kubernetes YAML Files
Create a new repository on GitHub to store the Kubernetes YAML files for deployment. These files will define the configurations for Pods, Services, Deployments, and other Kubernetes resources.

3. ## Writing a Kubernetes Manifest for Deployments
The Kubernetes deployment manifest defines the desired state of the application Pods in the cluster, including container image specifications, replicas, environment variables, and resource requirements. Write a deployment YAML file for each service in your application.

4. ## Writing a Kubernetes Manifest for Services
Create Kubernetes service manifest files to expose the microservices in the cluster. Services define the way that Pods communicate with each other or with external users.

5. ## Create EKS Cluster Using eksctl
Use eksctl to create your EKS cluster. This command will automatically create the necessary infrastructure (VPC, subnets, security groups) and set up the EKS control plane.

Command: 
eksctl create cluster --name voting-app-cluster --region us-west-2 --nodes 3 --node-type t2.medium --with-oidc

6. ## Create & Associate IAM OIDC Provider for Your EKS Cluster
In this step, create and associate an IAM OIDC provider for your EKS cluster to allow IAM roles for service accounts. This is required for controlling access between Kubernetes workloads and AWS services.

7. ## Create EC2 Keypair
You’ll need an EC2 keypair for SSH access to the instances in your EKS cluster. Create a new keypair using the AWS Management Console or AWS CLI.


Command:
aws ec2 create-key-pair --key-name voting-app-key --query 'KeyMaterial' --output text > voting-app-key.pem

8. ## Create Node Group with Additional Add-ons in Public Subnets
Create an EKS node group to run your application Pods. Make sure to include add-ons like aws-ebs-csi-driver and configure the group to use public subnets for internet-facing services.

9. ## Verify Cluster & Nodes
After creating the cluster, use kubectl to verify that your nodes and cluster are set up correctly:

Command:
kubectl get nodes

Ensure that the nodes show up as Ready.

10. ## Verify Cluster, Nodegroup in EKS Management Console
Go to the AWS Management Console and navigate to the EKS service. Verify that the cluster and node groups are up and running as expected.

11. ## Deployment of Pods into the EKS Cluster
Use the Kubernetes deployment YAML files to deploy the microservices (Voting-App, VotingResult-App, Worker-App, Redis) into the EKS cluster:

Commands:
kubectl apply -f deployment-voting-app.yaml
kubectl apply -f deployment-votingresult-app.yaml
kubectl apply -f deployment-worker-app.yaml
kubectl apply -f deployment-redis.yaml

12. ## Deployment of Services to the EKS Cluster
Once the Pods are deployed, expose the services using Kubernetes service manifests:

Commands:
kubectl apply -f service-voting-app.yaml
kubectl apply -f service-votingresult-app.yaml
kubectl apply -f service-worker-app.yaml
kubectl apply -f service-redis.yaml

These services will handle internal and external traffic routing to the Pods.

# Conclusion
By following this guide, you have successfully deployed a sample voting application with a microservices architecture on Kubernetes using Amazon EKS. This project demonstrates key concepts of cloud-native development, microservices orchestration, and the power of Kubernetes in managing containerized applications at scale.

Feel free to explore and modify the Kubernetes YAML files, or adapt the project for other microservices applications. Happy learning!

This README file provides a structured, easy-to-follow guide to your project, highlighting all the important steps for deploying microservices on EKS. It’s professional, clear, and well-organized for GitHub users.
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
