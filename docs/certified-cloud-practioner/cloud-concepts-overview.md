# Cloud Concepts Overview

> Cloud computing is the **on-demand** delivery of computing services over the **internet** with **pay-as-you-go** pricing.

## Introduction to Cloud Computing

### Types of Cloud Computing

#### Software as a Service (SaaS)

- Fully managed products.
- Least control over IT resource.
- Suitable for end-users.
- Service provider runs and maintains the software.
- Focus is on using the software.
- Users don't need to conern themselves with the maintenace or instrastructure.

#### Platform as a Service (PaaS)

- Abstracts underlying infrastructure management.
- Medium control over IT resource.
- Suitable for developers.
- Eliminates the eneed to handle hardware and operation system.
- Allow developers to concentrate on application development.

#### Infrastructure as a Service (IaaS)

- Fundamental cloud components.
- Most control over IT resource.
- Suitable for personnels seeking control and customization.
- High flexibility and control over resources.
- Includes networking, computers, and data storage.
- No involvement of data centers or hardwares is required.

### Cloud Computing Deployment Models

#### Public Cloud

- Services hosted and managed by the Cloud Service Provider (CSP).
- Also known as **Cloud-Native** or **Cloud First**.
- Suitable for new projects or those transitioning from a Virtual Private Server (VPS) to a CSP.

#### Private Cloud

- Services run on a company's own data centers.
- Also known as **On-Premise**.
- May use software like OpenStack.
- Used when organizations can't run on the cloud due to strict regulatory compliance or the sheer size of their organization.

#### Hybrid

- Combination of **On-Premise** and **Cloud Service Provider**.
- Ideal for organizations with their own data centers, or those unable to move everything to the cloud due to migration efforts or security compliance.

#### Traditional IT vs AWS

| Types | Tradition Examples | AWS |
| ----- | ------------------ | --- |
| Security | Firewalls, ACLs, Administrators | Security Groups, Network ACLs, IAM |
| Networking | Router, Network Pipeline, Switch | Elastic Load Balancing, Amazon VPC |
| Compute | On-premise servers | AMI, EC2 |
| Storage and Database | DAS, SAN, NAS, RDBMS | Amazon EBS, Amazon EFS, Amazon S3 | Amazon RDS |

## Advantages of Cloud Computing

### Agility

- Easy access to a range of technology.
- Rapid provisioning of resources.
- Reduces time from idea to implementation.

### Elasticity

- Eliminates the need for upfront resource over-provisioning.
- Provisions resources based on actual needs to avoid waste.
- Scalability allows for instant adjustments to resource capacity.

### Cost Saving

- Shifts from fixed expenses to variable expenses based on actual usage.
- Typically lower expenses due to economies of scale.
- Eliminates the need for maintaining data centers and physical servers.
- Reduces upfront investment.

### Deploy Globally in Minutes

- Access to global infrastructure.
- Enables rapid expansion and deployment in multiple locations.
- Reduces latency and improves end-user experience.

## Introduction to Amazon Web Services (AWS)

> AWS is a web service offering a standardized format for API interactions and a secure cloud platform with a broad set of global cloud-based products.

### What is AWS

- A secure cloud platform offering a broad set of global cloud-based products.
- Provides on-demand resources.
- Flexible and easy to use.
- Pay based on the duration of the services used.
- Products can be used together like building blocks.

### AWS Services

List of services provided by AWS.

### AWS Interaction

Methods to interact with AWS:

- AWS Management Console
- Command Line Interface (AWS CLI)
- Software Development Kits (SDKs)

## The AWS Cloud Adoption Framework (AWS CAF)

AWS CAF offers guidance and best practices for cloud adoption, with six core perspectives divided into business and technical capabilities.

### Business Capabilities

1. **Business:** Aligning IT with business needs.
1. **People:** Focus on training, staffing, and organizational changes.
1. **Governance:** Aligning IT strategy with business strategy and goals.

### Technical Capabilities

1. **Platform:** Understanding and communicating IT systems and their relationships. Describing the target state environment architecture.
1. **Security:** Ensuring security objectives are met.
1. **Operations:** Defining day-to-day, quarterly, and annual business operations.

## Core Cloud Services Offerings

### Compute

> Provides a virtual computer to run applications, programs, and code.

### Networking

> Offers a virtual network for internet connections or network isolations between services or outbound to the internet.

### Storage

> Acts as a virtual hard drive for file storage.

### Database

> Provides a virtual database for data storage.

## Amazon Web Services Overview

> Amazon Web Services (AWS) is a **Cloud Service Provider** (CSP) that provides **Infrastructure as a Service** (IaaS), among other services.

AWS services can be mapped to the 4 core cloud service offerings as follows:

| Core Cloud Service | Amazon Web Services         |
| ------------------ | --------------------------- |
| Compute            | **EC2** Virtual Machines    |
| Storage            | **EBS** Virtual Hard Drives |
| Database           | **RDS** SQL Databases       |

## Best Practices

- It is recommended to run a single application per instance to ensure efficient resource utilization and easier scalability and prevent dependency related issues.

## Dedicated vs VMs vs Containers vs Functions

### Dedicated Machines

- Dedicated machines are **physical servers** utilized exclusively by a **single customer**.
- The capacity is **fixed and predetermined**.
- There's a risk of **overpaying for underutilized** resources.
- Scaling resources requires **physical hardware changes**, often involving migration.
- Limited by the capabilities of the **host operating system**.

### Virtual Machines

- Run on a hypervisor, an underlying software layer that manages multiple virtual machines.
- A single physical server can be shared by multiple customers.
- Customers pay for only a fraction of the server, reducing costs for underutilized resources.
- Virtual Machines are limited by the guest operating system.
- Simplifies exporting or importing images for migration.
- Offers easier vertical and horizontal scaling options.

### Containers

- Containers operate on top of Virtual Machines or Dedicated Machines.
- The **Docker Daemon** is a common software layer enabling multiple containers to run concurrently.
- Containers share the same underlying OS kernel, optimizing resource utilization.
- More cost-effective, maximizing the use of available capacity.
- Allow running multiple applications side by side without inter-application dependency or configuration conflicts.

### Functions

- Functions run in a managed container environment, often referred to as Serverless Computing.
- Users upload code and specify memory and execution duration.
- Responsibility is limited to the code and data, not the underlying infrastructure.
- Cost-effective, as charges are based only on the execution time of the code.
- Cold starts can be a side-effect, causing latency during the initial run of a function.
