# Project Title: Static Website Deployment on AWS

## Overview

This project involves deploying a static HTML web app on AWS using various services and resources. The deployment script provided automates the process of setting up the web app on an EC2 instance. The infrastructure is designed as a 2-tier AWS network with a VPC, private and public subnets, NAT Gateways, Security Groups, Route Tables, an Application Load Balancer (ALB), and an Auto Scaling Group (ASG) for high availability.

## Project Components

### 1. Network Setup

- **VPC (Virtual Private Cloud):** Created a 2-tier VPC to isolate resources.

- **Subnets:** Set up private and public subnets for enhanced security.

- **NAT Gateways:** Implemented NAT Gateways for private subnet access to the internet.

### 2. Security

- **Security Groups:** Configured security groups to control inbound and outbound traffic.

### 3. Route Management

- **Route Tables:** Established route tables for proper routing within the VPC.

### 4. Load Balancing

- **ALB (Application Load Balancer):** Deployed an ALB to distribute traffic across multiple instances.

- **Target Groups:** Configured target groups to route traffic to specific instances.

### 5. Domain Management

- **Route 53:** Used Route 53 to manage the domain and create a Record Set for routing traffic.

### 6. SSL Certificate

- **AWS Certificate Manager:** Registered and configured an SSL certificate for secure HTTPS communication.

### 7. Auto Scaling

- **Launch Template and ASG (Auto Scaling Group):** Set up an Auto Scaling Group with a Launch Template for automated scaling and increased availability.

## Deployment Script

```bash
sudo su
yum update -y
yum install -y httpd
cd /var/www/html
wget https://github.com/Yemiter/techmax/archive/refs/heads/main.zip
unzip main.zip
cp -r techmax-main/* /var/www/html
rm -rf techmax-main main.zip
systemctl enable httpd
systemctl start httpd
```

This script installs Apache (httpd), retrieves the web app code from the specified GitHub repository, and configures Apache to serve the content.

## Steps to Replicate

1. **Network Setup:**
   - Create a new VPC.
   - Configure private and public subnets.
   - Set up NAT Gateways for private subnet internet access.

2. **Security Setup:**
   - Configure Security Groups for instances.

3. **Route Configuration:**
   - Set up Route Tables for proper routing.

4. **Load Balancer:**
   - Create an ALB with associated target groups.

5. **Domain Configuration:**
   - Use Route 53 to manage the domain and create a Record Set.

6. **SSL Certificate:**
   - Register for an SSL certificate in AWS Certificate Manager.

7. **Auto Scaling:**
   - Create a Launch Template and an Auto Scaling Group for increased availability.

8. **Deploy the Web App:**
   - Execute the provided deployment script on the EC2 instance.

Now, your static website should be accessible via the configured domain over HTTPS through the ALB. The Auto Scaling Group ensures high availability by automatically adjusting the number of instances based on demand.
