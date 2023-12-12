# Cloud Economics and Billing

## Fundamentals of Pricing

### AWS Pricing Model

The total cost in AWS is determined by three fundamental drivers of cost

1. Compute

    - Charged per hour or second, varies by instance type.

1. Storage

    - Charged per GB.

1. Data Transfer

    - Outbound transfer is aggregated and charged, typically per GB.
    - Inbound transfer is usually free, with some exceptions.

### Pay Less When You Reserve

- Achieve savings by reserving resources in advance.

#### Reserved Instances (RIs)

- Reserved Instances can offer up to 72% savings compared to on-demand pricing.
- Commitment is made for a specific amount over a specified term (e.g., 1 year or 3 years).
- RI Types:
    - **All Upfront Reserved Instances (AURI):** Full payment is made upfront.
    - **Partial Upfront Reserved Instance (PURI):** Partial payment is made upfront, with the rest paid over time.
    - **No Upfront Payments Reserved Instances (NURI):** No upfront payment; costs are spread over the term.

### Pay Less By Using More

Increased usage leads to greater savings, applicable to tiered pricing services like S3, EBS, EFS.

### Pay Less As AWS Grows

Economies of scale: AWS passes savings from its growth back to customers.

### AWS Free Tier

Offers new customers certain services free for a limited time (e.g., a year).
Some services are always free within specified limits (e.g., Amazon VPC, IAM).

## Total Cost of Ownership (TCO)

- A financial estimate to identify direct and indirect costs of a system.
- Useful for comparing on-premises infrastructure costs with cloud-based solutions.
- Often used to justify the move to cloud computing.

### TCO Considerations

#### Compute

- Hardware costs (servers).
- Software costs (OS, virtualization licenses, maintenance).
- Facilities costs (space, power, cooling).

#### Storage and Database

- Hardware costs (storage devices).
- Storage administration costs.
- Facilities costs (space, power, cooling).

#### Network Costs

- Hardware costs (switches, load balancers).
- Network administration costs.
- Bandwidth costs.
- Facilities costs (space, power, cooling).

#### IT Labor Costs

- Costs associated with server, storage, network, and database administration.

### AWS Pricing Calculator

See [AWS Pricing Calculator](https://calculator.aws)

- Online tool to estimate monthly AWS costs.
- Helps identify cost-saving opportunities.
- Offers detailed price points and calculations.
- Includes instance types and contract terms options.
- Allows naming and grouping of service estimates.

## AWS Organisations

### Features and Benefits

- Centralized policy-based account management.
- Group-based account management.
- Automation of account management through APIs.
- Consolidated billing across multiple accounts.

### Security with AWS Organisations

- Access control using IAM policies.
- Service control policies (SCPs) to manage access across the organization.

### Organizations Setup

1. Create an organization.
1. Establish organizational units (OUs).
1. Implement service control policies.
1. Test access restrictions and policy compliance.

### AWS Organizations Limitations

#### Naming Limits

Names must consist of Unicode characters, with a maximum of 250 characters.

#### Maximum and Minimum Values

Limits on the number of AWS accounts, roots, OUs, policies, policy document size, OU nesting levels, daily invitations, and concurrent account creation processes.

## AWS Billing and Cost Management

- **AWS Budgets:** Track and manage budgets.
- **AWS Cost and Usage Report:** Detailed usage and cost data.
- **AWS Cost Explorer:** Analyze and visualize spending patterns.

## Technical Support

AWS offers various support tools and professional assistance:

- **AWS Support:** Technical assistance for AWS services.
- **Technical Account Manager (TAM):** Proactive guidance and support.
- **AWS Trusted Advisor:** Best practices recommendations.
- **AWS Support Concierge:** Dedicated account assistance.

### AWS Support Plans

Four levels of support plans are available:

1. **Basic Support:** Access to resource center, service health dashboard, FAQs, discussion forums, health checks.
1. **Developer Support:** Ideal for early development stages on AWS.
1. **Business Support:** Suitable for customers running production workloads.
1. **Enterprise Support:** Designed for customers with business and mission-critical workloads.

| Support Plans | Critical (15 Minutes) | Urgent (1 Hour) | High (4 Hours) | Normal (12 Hours) | Low (24 Hours) |
| ------------- | -------- | ------ | ---- | ------ | --- |
| Basic | - | - | - | - | - |
| Developer Plan (Business Hours) | - | - | - | Yes | Yes |
| Business Plan (24/7) | - | Yes | Yes | Yes | Yes |
| Enterprise Plan (24/7) | Yes | Yes | Yes | Yes | Yes |
