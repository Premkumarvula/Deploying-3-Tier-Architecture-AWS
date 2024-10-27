# About 3-Tier Architecture
![image](https://github.com/user-attachments/assets/08521b10-0e41-4435-a4d9-4291931009b4)

## Project Overview
The goal is to create a three-tier architecture on AWS, consisting of a web tier, application (app) tier, and database (DB) tier. Each tier is responsible for different parts of the application stack.

## Tier Breakdown
- **Web Tier**: Uses nginx as the web server on port 80, and Node.js (React) for the front end.
- **App Tier**: Uses Node.js as the backend application server on port 4000 and MySQL to interact with the database.
- **DB Tier**: Uses Amazon RDS (MySQL) for the database. RDS is managed by AWS, handling updates, patches, and auto-scaling. The database is configured as a multi-AZ deployment to ensure high availability.

## Purpose and Benefits
- **High Availability**: By deploying resources across multiple Availability Zones (AZs), the system remains accessible even if one AZ fails.
- **Fault Tolerance**: Uses auto-scaling for both web and app servers, and multi-AZ deployment for the database to handle failures.
- **Security**: Limits access by setting security groups:
  - Only the web tier can access the app tier on port 4000.
  - Only the app tier can access the DB tier on port 3306.

# Deploying-3-Tier-Architecture-AWS
This project demonstrates the deployment of a scalable and highly available web application infrastructure on AWS. The architecture utilizes several key AWS services to ensure performance, reliability, and security.

# Architecture Overview
![image](https://github.com/user-attachments/assets/c1c242ea-10aa-476b-95e7-23e951effc2f)

In this architecture, a public-facing Application Load Balancer forwards client traffic to our web tier EC2 instances. The web tier is running Nginx webservers that are configured to serve a React.js website and redirects our API calls to the application tier’s internal facing load balancer. The internal facing load balancer then forwards that traffic to the application tier, which is written in Node.js. The application tier manipulates data in an Aurora MySQL multi-AZ database and returns it to our web tier. Load balancing, health checks and autoscaling groups are created at each layer to maintain the availability of this architecture.

# AWS Infrastructure Setup

## AWS Services Used

### Amazon EC2 (Elastic Compute Cloud)
Provides resizable compute capacity in the cloud, hosting the application servers.

### Auto Scaling Group (ASG)
Automatically adjusts the number of EC2 instances based on traffic demands, ensuring cost-efficiency and optimal performance.

### Application Load Balancer (ALB)
Distributes incoming application traffic across multiple targets, such as EC2 instances, enhancing fault tolerance and availability.

### AWS Identity and Access Management (IAM)
Manages user access and permissions securely, ensuring proper governance of AWS resources.

### Amazon S3 (Simple Storage Service)
Stores and retrieves any amount of data at any time, serving as the primary storage for static assets like images and videos.

### Amazon EFS (Elastic File System)
Provides scalable and shared file storage accessible from multiple EC2 instances, facilitating easy data sharing across the application.

### Amazon RDS (Relational Database Service)
Simplifies database management, enabling scalable and highly available relational databases.

### Amazon VPC (Virtual Private Cloud)
Creates a secure and isolated network environment, giving control over the network topology and enhancing security.

### Amazon CloudWatch
Monitors application performance and resource utilization, offering alerts and logging for operational insights.

### Amazon SNS (Simple Notification Service)
Sends notifications and messages to users or other services based on events, enhancing communication and responsiveness.

### AWS CloudTrail
Logs all API calls and actions in the AWS account, supporting auditing, compliance, and governance needs.

### Amazon Route 53
Provides DNS services for reliable domain name resolution, directing users to the application endpoints.

### Amazon CloudFront
A content delivery network (CDN) that speeds up the delivery of your web content by caching it at edge locations around the world.

### AWS WAF (Web Application Firewall)
Protects web applications from common web exploits that could compromise security or availability.

### AWS Shield
Provides advanced protection against Distributed Denial of Service (DDoS) attacks, ensuring application uptime and security.
