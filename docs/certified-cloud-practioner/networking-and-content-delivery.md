# Networking and Content Delivery

## Networking Basics

### Classless Inter-Domain Routing (CIDR)

- CIDR is a method for allocating IP addresses and routing IP packets.
- It is used to create unique identifiers for networks and individual devices.
- The CIDR notation includes an IP address and a suffix indicating the number of bits used for the network portion.

For example, in `198.51.100.24/24`

| Type              | Decimal          | Binary                                |
| ----------------- | ---------------- | ------------------------------------- |
| IP                | `198.51.100.24`  | `11000110 00110011 01100100 00011000` |
| Bit Mask          | `198.51.100.0`   | `11111111 11111111 11111111 00000000` |
| Network Address   | `198.51.100.0`   | `11111111 11111111 11111111 00000000` |
| Broadcast Address | `198.51.100.255` | `11000110 00110011 01100100 11111111` |

- The subnet mask `/24` indicates that the first 24 bits are used for network address
- The network address is the bit mask
- The broadcast address is the result of the bitwise and operation of the IP address and the 1s complement of bitmask 

### Open Systems Interconnection (OSI)

| Layer | Level | Description | Protocol Data Unit (PDU) |
| ----- | ----- | ----------- | -------- |
| Physical Layer  | 1 | Handles the physical connection between devices | Bit, Symbol |
| Data Link Layer | 2 | Transmission of data frames between two adjacent network nodes, e.g. MAC | Frame |
| Network Layer   | 3 | Handles packet forwarding including routing through intermediate routers, e.g. IP | Packet |
| Transport       | 4 | Transmission of data segments in a network, i.e. segmentation, acknowledgement, multiplexing | Segment, Datagram |
| Session         | 5 | Manages sessions between end-user applications | Data |
| Presentation    | 6 | Translation of data between a networking service and an application; i.e. encoding, compression, encryption/decryption | Data |
| Application     | 7 | High-level protocols such as for resource sharing or remote file access, e.g. HTTP. | Data |

## Amazon VPC

Amazon VPC allows you to provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you define.

### VPC Characteristics

- **Isolation:** Each VPC is isolated from other virtual networks in the AWS Cloud.
- **Region-specific:** Resides within a single AWS region.
- **Multiple Availability Zones:** Can span multiple Availability Zones within that region.

### Subnets

- **Division of VPC:** A subnet is a range of IP addresses in your VPC.
- **Availability Zone Specific:** A subnet must reside within one Availability Zone and cannot span zones.
- **Public or Private:** Depending on the route table and internet gateway settings.

### IP Addressing

- **CIDR Block Assignment:** Assign a CIDR block to your VPC.
- **IPv4 and IPv6:** Supports both IPv4 and IPv6 addresses.
- **Non-overlapping Subnets:** Subnet CIDR blocks must not overlap.
- The allowed IPv4 CIDR block size for a subnet is between a /28 netmask and /16 netmask.
- Address range cannot be altered after creation

### Reserved IP Address

- **First Four and Last One:** In each subnet, AWS reserves the first four IP addresses and the last IP address.
- **Examples:** In a 10.0.0.0/24 subnet, the addresses 10.0.0.0, 10.0.0.1, 10.0.0.2, 10.0.0.3, and 10.0.0.255 are reserved.

### Public IP Address Types

#### Public IPv4 Address

- **Assignment:** Can be assigned manually (Elastic IP) or automatically (auto-assign at subnet level).
- **Use Case:** Required for communication with the internet.

#### Elastic IP Address

- **AWS Account Association:** Allocated to an AWS account, and can be remapped.
- **Flexibility:** Can be moved between instances.
- **Charges:** Additional charges may apply for idle Elastic IPs.

### Elastic Network Interface (ENI)

- **Virtual Network Interface:** Can be attached to instances within a VPC.
- **Flexibility:** Can be detached and attached to different instances.
- **Attributes:** Include a primary private IP address, one or more secondary private IP addresses, an Elastic IP address, and more.
- Attribiutes follows when attached to new instance

### Route Tables and Routes

- **Route Table Configuration:** Contains rules for directing network traffic.
- **Destination and Target:** Each route in a table specifies a destination and a target.
- **Default Route Table:** Every VPC has a default route table for local routing within the VPC.
- **Association with Subnets:** Each subnet must be associated with one and only one route table.

## VPC Networking

### Internet Gateway

### Network Address Translation (NAT) Gateway

### VPC Sharing

### VPC Peering

### AWS Site-to-Site VPN

### AWS Direct Connect

### VPC Endpoints

### AWS Transit Gateway

## VPC Security

### Security Groups

- **Instance-Level:** Security groups act at the instance level, controlling inbound and outbound traffic for individual instances.
- **Default Rules:** By default, security groups deny all inbound traffic and allow all outbound traffic.
- **Stateful:** Security groups are stateful, meaning if you allow inbound traffic from a specific source, the corresponding outbound reply traffic is automatically allowed.

#### Inbound Rules Table

| Source | Protocol | Port Range | Description |
| ------ | -------- | ---------- | ----------- |
| sg-xxx | All      | All        | Allow inbound traffic from instances assigned to the same security group |

#### Outbound Rules Table

| Source      | Protocol | Port Range | Description                     |
| ----------- | -------- | ---------- | ------------------------------- |
| `0.0.0.0/0` | All      | All        | Allow all outbound IPv4 traffic |
| `::/0`      | All      | All        | Allow all outbound IPv6 traffic |

### Custom Security Groups

- **Allow Rules Only:** You can specify allow rules for inbound traffic, but you cannot define deny rules.
- **Rule Evaluation:** All rules are evaluated, and if any rule allows the traffic, it is permitted.

#### Inbound Rules Table

| Source           | Protocol | Port Range | Description |
| ---------------- | -------- | ---------: | ----------- |
| `0.0.0.0/0`      | TCP      | 80         | Allow inbound HTTP access from all IPv4 addresses |
| `0.0.0.0/0`      | TCP      | 443        | Allow inbound HTTPS access from all IPv4 addresses |
| `192.168.1.0/24` | TCP      | 22         | Allow inbound SSH access to Linux instance from IPv4 IP address in the network |

#### Outbound Rules Table

| Source      | Protocol | Port Range | Description                     |
| ----------- | -------- | ---------- | ------------------------------- |
| sg-xxx | TCP      | 1433        | Allow all outbound SQL access to instances in the specified in the security group |

### Network Access Control Lists (Network ACL)

- **Subnet-Level:** Network ACLs act at the subnet level, controlling traffic for all instances in the subnet.
- **Inbound and Outbound Rules:** Network ACLs have separate rules for inbound and outbound traffic.
- **Stateless:** Unlike security groups, Network ACLs are stateless, and you must define rules for both directions (inbound and outbound).

#### Inbound Rules Table

| Rule | Type             | Protocol | Port Range | Source      | Allow/Deny |
| ---- | ---------------- | -------- | ---------- | ----------- | ---------- |
| 100  | All IPv4 Traffic | All      | All        | `0.0.0.0/0` | Allow      |
| *    | All IPv4 Traffic | All      | All        | `0.0.0.0/0` | Deny       |

#### Outbound Rules Table

| Rule | Type             | Protocol | Port Range | Source      | Allow/Deny |
| ---- | ---------------- | -------- | ---------- | ----------- | ---------- |
| 100  | All IPv4 Traffic | All      | All        | `0.0.0.0/0` | Allow      |
| *    | All IPv4 Traffic | All      | All        | `0.0.0.0/0` | Deny       |

### Custom Network ACL

- **Initial Deny:** Custom Network ACLs deny all inbound and outbound traffic until you add explicit allow rules.
- **Rule Evaluation:** Rules are evaluated in number order, and the first matching rule decides whether to allow or deny traffic.

#### Inbound Rules Table

| Rule | Type             | Protocol | Port Range | Source         | Allow/Deny |
| ---- | ---------------- | -------- | ---------: | -------------- | ---------- |
| 100  | HTTPS            | TCP      | 443        | `0.0.0.0/0`    | Allow      |
| 120  | SSH              | TCP      | 22         | `192.0.2.0/24` | Allow      |
| *    | All IPv4 Traffic | All      | All        | `0.0.0.0/0`    | Deny       |

#### Outbound Rules Table

| Rule | Type             | Protocol | Port Range | Source         | Allow/Deny |
| ---- | ---------------- | -------- | ---------: | -------------- | ---------- |
| 100  | HTTPS            | TCP      | 443        | `0.0.0.0/0`    | Allow      |
| 120  | SSH              | TCP      | 22         | `192.0.2.0/24` | Allow      |
| *    | All IPv4 Traffic | All      | All        | `0.0.0.0/0`    | Deny       |

### Security Groups vs Network ACL

| Attribute | Security Groups | Network ACLs |
| --------- | --------------- | ------------ |
| Scope | Individual instances | Subnet level, affecting all instances within it. |
| Allow rules | Yes | Yes |
| Deny rules | No | No |
| State | Stateful | Stateless |
| Order of Rules | Evaluated collectively; Unordered. | Evaluated in ascending order by rule number. |
| Default Inbound Behavior | Deny all inbound traffic | Allow all inbound |
| Default Outbound Behavior | Allow all outbound traffic | Allow outbound traffic |
| Customization | Control inbound/outbound traffic control | Broader subnet-level restrictions |
| Use Case | Managing traffic to individual instances | Additional layer of defense at the subnet level |

## Amazon Route 53

- Highly available and scalable Domain Name System (DNS) web service
- Designed for routing end users to Internet applications by translating domain names into IP addresses.
- Supports both IPv4 and IPv6.

### Key Features

- **DNS Resolution:** Translates domain names like `www.google.com` into their corresponding IP addresses.
- **Health Checking:** Monitors the health of your resources and routes traffic only to healthy endpoints.
- **Traffic Management:** Offers various routing policies for managing traffic globally.
- **Domain Registration:** Allows you to register domain names.

### DNS Resolution Process

1. A user, like Bob, requests the IP address of `www.google.com`.
1. The DNS resolver queries Amazon Route 53 for the IP address.
1. Route 53 returns the IP address of www.google.com.
1. The DNS resolver provides Bob with the IP address.

### Amazon Route 53 Supported Routing

- **Simple Routing:** Ideal for single-resource environments.
- **Weighted Round Robin Routing:** Assigns weights to route traffic proportionally across multiple resources.
- **Latency Routing:** Routes traffic based on the lowest network latency for your end user.
- **Geolocation Routing:** Routes traffic based on the geographic location of your users.
- **Geoproximity Routing:** Routes traffic based on the geographic location of your resources and users.
- **Failover Routing:** Automatically routes traffic to a backup resource when the primary one is unavailable.
- **Multivalue Answer Routing:** Responds to DNS queries with multiple healthy resources.

## Amazon CloudFront

- Amazon CloudFront is a fast content delivery network (CDN) service
- Securely delivers data, videos, applications, and APIs to customers globally with low latency and high transfer speeds.

### Amazon CloudFront Key Characteristics

- **Global Network:** Consists of edge locations and regional edge caches for efficient content delivery.
- **Edge Locations:** Serve popular content directly to users nearby.
- **Regional Edge Cache:** Stores less frequently accessed content, acting as an intermediary cache layer.
- **Dynamic and Static Content Delivery:** Optimizes the delivery of both static and dynamic content.
- **Integration with AWS Services:** Deeply integrated with AWS services like S3, EC2, and AWS Shield for enhanced functionality.

### Amazon CloudFront Benefits

- **Performance:** Fast delivery of content with reduced latency.
- **Security:** Enhanced security features at the edge locations.
- **Programmability:** Customizable and programmable CDN solutions.
- **AWS Integration:** Seamless integration with AWS services and infrastructure.
- **Cost-Effectiveness:** Pay-as-you-go pricing model, without upfront costs.

### Amazon CloudFront Pricing

- **Data Transfer Out:** Based on the volume of data transferred out from CloudFront to end users.
- **HTTP(S) Requests:** Charges apply for the number of HTTP(S) requests made.
- **Invalidation Requests:** The first 1000 paths each month are free; subsequent paths incur a charge per path.
- **Dedicated IP Custom SSL:** Additional charges may apply for custom SSL certificates.
