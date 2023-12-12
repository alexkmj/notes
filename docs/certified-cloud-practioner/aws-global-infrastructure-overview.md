# AWS Global Infrastructure Overview

## AWS Global Infrastructure

- Designed to be **flexible**, **reliable**, **scalable**, and **secure**.
- It aims to provide high-quality **global network performance**.

### AWS Region

- **Data Replication:** Across regions for high availability.
- **Inter-Region Communication:** Utilizes AWS backbone network infrastructure.
- **Redundancy and Connectivity:** Each region is fully redundant, connected via availability zones for robustness.

### Selecting a region

Factors influencing region selection include:

- Data Governance and Legal Requirements
- Proximity to Customers
- Pricing can differ between regions.
- **Service Availability:** Some AWS services may not be available in all regions.

### Avaiability zones

- Each region comprises multiple availability zones.
- **Isolation:** Each zone is a fully isolated partition of the AWS infrastructure.
- **Data Centers:** Discrete data centers in each zone, designed for fault tolerance.
- **Networking:** High-speed private networking interconnects zones.
- **Data Replication:** Recommended across zones for enhanced resiliency.

### AWS Data Centers

- Focused on **security** and **redundancy**.
- Houses the physical servers and infrastructure.

### Points of Presence

- Caches content closer to users to improve performance.
- Includes **edge locations** and **regional edge caches**.
- Hosts Amazon CloudFront, a Content Delivery Network (CDN), for reduced latency.

## AWS Service and Service Category Overview

### AWS Storage Services

- Amazon Simple Storage Service (Amazon S3)
- Amazon Elastic Block Store (Amazon EBS)
- Amazon Elastic File System (Amazon EFS)
- Amazon Simple Storage Service Glacier

### AWS Compute Services

- Amazon EC2
- Amazon EC2 Auto Scaling
- Amazon Elastic Container Service (Amazon ECS)
- Amazon EC2 Container Registry
- AWS Elastic Beanstalk
- AWS Lambda
- Amazon Elastic Kubernetes Services (Amazon EKS)
- AWS Fargate

### AWS Database Services

- Amazon Relational Database Service
- Amazon Aurora
- Amazon Redshift
- Amazon DynamoDB

### AWS Networking and Content Delivery Services

- Amazon VPC
- Elastic Load Balancing
- Amazon CloudFront
- AWS Transit Gateway
- Amazon Route 53
- AWS Direct Connect
- AWS VPN

### AWS Security, Identity, and Compliance Services

- AWS Identity and Access Management (IAM)
- AWS Organizations
- Amazon Cognito
- AWS Artifact
- AWS Key Management Service
- AWS Shield

### AWS Cost Management Services

- AWS Cost and Usage Report
- AWS Budgets
- AWS Cost Explorer

### AWS Management and Governance Services

- AWS Management Console
- AWS Config
- Amazon CloudWatch
- AWS Auto Scaling
- AWS Command Line Interface
- AWS Trusted Advisor
- AWS Well-Architected Tool
- AWS CloudTrail
