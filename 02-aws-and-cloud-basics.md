# Chapter 2: AWS & Cloud Basics

---

## 2.1 What is Cloud Computing?

Cloud computing is the delivery of on-demand IT resources — compute, storage, networking, databases, and more — over the internet, with pay-as-you-go pricing. Instead of buying, owning, and maintaining physical data centers and servers, you access technology services from a cloud provider like AWS.

### Traditional IT vs. Cloud

| Traditional IT | Cloud Computing |
|---|---|
| Buy hardware upfront (CapEx) | Pay only for what you use (OpEx) |
| Weeks/months to provision | Provision in minutes |
| Fixed capacity — over/under provision | Scale up or down instantly |
| You manage hardware, OS, networking | Provider manages infrastructure |
| Single physical location | Global deployment in minutes |

---

## 2.2 Cloud Deployment Models

| Model | Description | Example |
|---|---|---|
| **Public Cloud** | Resources owned and operated by a third-party provider, shared across customers | AWS, Azure, GCP |
| **Private Cloud** | Cloud infrastructure operated solely for one organization | On-prem VMware, OpenStack |
| **Hybrid Cloud** | Combination of public and private cloud, connected together | AWS + on-premises data center via Direct Connect |
| **Multi-Cloud** | Using services from two or more cloud providers | AWS + Azure together |

---

## 2.3 Cloud Service Models

### IaaS — Infrastructure as a Service
- You manage: OS, middleware, runtime, data, applications
- Provider manages: Virtualization, servers, storage, networking
- Example: **AWS EC2** (you get a virtual machine, you manage everything on it)

### PaaS — Platform as a Service
- You manage: Applications and data
- Provider manages: Everything below the application layer
- Example: **AWS Elastic Beanstalk**, **AWS RDS**

### SaaS — Software as a Service
- You manage: Nothing (just use the software)
- Provider manages: Everything
- Example: **Gmail**, **Salesforce**, **AWS WorkMail**

```
Responsibility Stack:
┌─────────────────┐
│   Application   │  ← You own this in IaaS/PaaS; provider owns in SaaS
├─────────────────┤
│      Data       │  ← You always own your data
├─────────────────┤
│    Runtime      │  ← PaaS/SaaS: provider manages
├─────────────────┤
│  Middleware     │  ← PaaS/SaaS: provider manages
├─────────────────┤
│       OS        │  ← IaaS: you manage; PaaS/SaaS: provider manages
├─────────────────┤
│ Virtualization  │  ← Always provider-managed in cloud
├─────────────────┤
│ Servers/Storage │  ← Always provider-managed in cloud
└─────────────────┘
```

---

## 2.4 AWS Global Infrastructure

AWS operates one of the world's largest global cloud infrastructures. Understanding its structure is essential for designing resilient, high-performance applications.

### 2.4.1 Regions

A **Region** is a distinct geographic area (e.g., `us-east-1` = N. Virginia, `ap-south-1` = Mumbai). AWS currently has **36+ geographic regions** worldwide.

**How to choose a Region:**
- **Latency** — pick the region closest to your users
- **Compliance** — some data residency laws require data to stay in a specific country
- **Service availability** — not all services are available in every region
- **Pricing** — costs vary slightly by region

Common Regions:

| Region Code | Location |
|---|---|
| `us-east-1` | US East (N. Virginia) — default, most services launch here first |
| `us-west-2` | US West (Oregon) |
| `eu-west-1` | Europe (Ireland) |
| `ap-south-1` | Asia Pacific (Mumbai) |
| `ap-southeast-1` | Asia Pacific (Singapore) |

---

### 2.4.2 Availability Zones (AZs)

Each Region contains **multiple Availability Zones** (minimum 3). An AZ is one or more discrete data centers with redundant power, networking, and connectivity.

```
Region: ap-south-1 (Mumbai)
├── AZ: ap-south-1a  (Data Center cluster A)
├── AZ: ap-south-1b  (Data Center cluster B)
└── AZ: ap-south-1c  (Data Center cluster C)
```

- AZs within a Region are connected via **low-latency, high-bandwidth private fiber**
- Deploying across multiple AZs protects your application from a single data center failure
- This is the foundation of **High Availability (HA)** in AWS

---

### 2.4.3 Edge Locations

Edge locations are endpoints used for **content caching and delivery** (via Amazon CloudFront). There are **400+ edge locations** globally — far more than Regions — bringing content closer to end users for lower latency.

```
Infrastructure Hierarchy:
Regions (36+) → Availability Zones (114+) → Edge Locations (400+)
```

---

## 2.5 AWS Shared Responsibility Model

Security in AWS is a **shared responsibility** between AWS and you (the customer).

```
┌──────────────────────────────────────────────────────────┐
│                    CUSTOMER RESPONSIBILITY                │
│  "Security IN the cloud"                                  │
│  - Data encryption (at rest and in transit)              │
│  - IAM users, roles, and policies                        │
│  - OS patches on EC2 instances                           │
│  - Application security                                   │
│  - Network and firewall configuration (Security Groups)  │
├──────────────────────────────────────────────────────────┤
│                      AWS RESPONSIBILITY                   │
│  "Security OF the cloud"                                  │
│  - Physical data center security                         │
│  - Hardware and global infrastructure                    │
│  - Managed service software (e.g., RDS database engine)  │
│  - Network infrastructure and hypervisor                 │
└──────────────────────────────────────────────────────────┘
```

> **Simple rule:** AWS secures the infrastructure. You secure what you build and deploy on it.

---

## 2.6 Core AWS Services

### 2.6.1 Compute

#### Amazon EC2 (Elastic Compute Cloud)
Virtual servers in the cloud. You choose the OS, CPU, RAM, and storage.

- **Instance Types:** General purpose (t3, m6i), Compute optimized (c6i), Memory optimized (r6i), Storage optimized (i3)
- **Pricing Models:**
  - *On-Demand* — pay per second, no commitment
  - *Reserved* — up to 72% savings with 1 or 3-year commitment
  - *Spot* — up to 90% savings using spare AWS capacity (can be interrupted)
  - *Savings Plans* — flexible discount plans

**Key concepts:**
- **AMI (Amazon Machine Image):** A pre-configured OS template used to launch instances
- **Security Groups:** Virtual firewalls that control inbound/outbound traffic to instances
- **Key Pairs:** SSH keys used to securely connect to Linux EC2 instances
- **Elastic IP:** A static public IP address you can attach to an instance

---

#### AWS Lambda
Serverless compute — run code without managing servers. You upload your function, AWS runs it in response to events.

- Supports: Python, Node.js, Java, Go, .NET, Ruby
- Billed per invocation and execution duration (milliseconds)
- Max execution time: 15 minutes
- **Use case:** Event-driven tasks, API backends, scheduled jobs

---

#### Amazon ECS / EKS
Container orchestration services.
- **ECS (Elastic Container Service):** AWS-native Docker container management
- **EKS (Elastic Kubernetes Service):** Managed Kubernetes

---

### 2.6.2 Storage

#### Amazon S3 (Simple Storage Service)
Object storage — store and retrieve any amount of data at any time.

- Stores data as **objects** inside **buckets**
- Virtually unlimited storage
- 99.999999999% (11 nines) durability
- Access control via bucket policies and ACLs

**S3 Storage Classes (cost optimization):**

| Class | Use Case |
|---|---|
| S3 Standard | Frequently accessed data |
| S3 Standard-IA | Infrequently accessed, rapid retrieval |
| S3 One Zone-IA | Non-critical, infrequent access |
| S3 Glacier Instant Retrieval | Archive with millisecond retrieval |
| S3 Glacier Flexible Retrieval | Archive, retrieval in minutes to hours |
| S3 Glacier Deep Archive | Lowest cost, 12-48 hour retrieval |

---

#### Amazon EBS (Elastic Block Store)
Persistent block storage attached to EC2 instances — like a hard drive for your virtual server.

- Exists independently of the EC2 instance lifecycle
- Types: gp3 (general purpose SSD), io2 (high IOPS), st1 (throughput HDD)

---

#### Amazon EFS (Elastic File System)
Managed NFS (Network File System) that can be shared across multiple EC2 instances simultaneously.

---

### 2.6.3 Networking

#### Amazon VPC (Virtual Private Cloud)
Your own isolated virtual network within AWS. Everything in AWS runs inside a VPC.

```
VPC (10.0.0.0/16)
├── Public Subnet (10.0.1.0/24)   ← Internet-facing resources (web servers)
│   └── Internet Gateway           ← Entry/exit point to the internet
└── Private Subnet (10.0.2.0/24)  ← Internal resources (databases)
    └── NAT Gateway                ← Allows private subnet to reach internet (outbound only)
```

**Key VPC components:**

| Component | Purpose |
|---|---|
| **Subnet** | A range of IP addresses within a VPC (public or private) |
| **Internet Gateway (IGW)** | Allows communication between VPC and the internet |
| **NAT Gateway** | Allows private subnets to initiate outbound internet access |
| **Route Table** | Controls where network traffic is directed |
| **Security Groups** | Stateful firewall at the instance level |
| **Network ACLs** | Stateless firewall at the subnet level |

---

#### Amazon Route 53
Highly available and scalable DNS (Domain Name System) web service. Also supports health checks and traffic routing policies (latency-based, failover, geolocation).

---

#### Amazon CloudFront
Content Delivery Network (CDN). Distributes content from 400+ edge locations globally for low-latency delivery.

---

### 2.6.4 Databases

#### Amazon RDS (Relational Database Service)
Managed relational databases. Supports MySQL, PostgreSQL, MariaDB, Oracle, SQL Server, and Amazon Aurora.

- AWS handles: backups, patching, hardware provisioning, replication
- You handle: schema design, query optimization, application code

#### Amazon DynamoDB
Fully managed NoSQL database. Single-digit millisecond performance at any scale.
- Key-value and document data model
- Serverless — no servers to manage

#### Amazon ElastiCache
Managed in-memory caching (Redis or Memcached). Used to speed up application performance.

---

### 2.6.5 Security & Identity

#### AWS IAM (Identity and Access Management)
Controls **who** (authentication) can do **what** (authorization) in AWS.

**Core IAM concepts:**

| Concept | Description |
|---|---|
| **User** | A person or application with long-term credentials |
| **Group** | A collection of users sharing the same permissions |
| **Role** | Temporary credentials assumed by AWS services or users |
| **Policy** | JSON document defining permissions (Allow/Deny actions on resources) |

**IAM Best Practices:**
- Enable MFA for all users
- Follow the **Principle of Least Privilege** — grant only the permissions needed
- Never share access keys
- Rotate credentials regularly
- Use IAM Roles for applications running on EC2

**Example IAM Policy (read-only S3 access):**
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:ListBucket"
      ],
      "Resource": [
        "arn:aws:s3:::my-bucket",
        "arn:aws:s3:::my-bucket/*"
      ]
    }
  ]
}
```

---

### 2.6.6 Monitoring & Management

#### Amazon CloudWatch
Monitoring and observability service.
- Collects **metrics** from AWS services (CPU, memory, request counts)
- Stores **logs** from applications and AWS services
- Sets **alarms** that trigger actions (e.g., auto-scaling, SNS notifications)
- Creates **dashboards** for visual monitoring

#### AWS CloudTrail
Logs every API call made in your AWS account — who did what, when, and from where. Essential for auditing and security investigations.

#### AWS Config
Records and evaluates AWS resource configurations over time. Helps with compliance and change management.

---

## 2.7 AWS Well-Architected Framework

AWS defines 6 pillars for building well-architected cloud systems:

| Pillar | Focus |
|---|---|
| **Operational Excellence** | Run and monitor systems, continuously improve processes |
| **Security** | Protect data, systems, and assets |
| **Reliability** | Recover from failures, meet demand dynamically |
| **Performance Efficiency** | Use resources efficiently as demand changes |
| **Cost Optimization** | Avoid unnecessary costs |
| **Sustainability** | Minimize environmental impact |

> Use the **AWS Well-Architected Tool** (free in the console) to review your workloads against these pillars.

---

## 2.8 AWS Pricing Fundamentals

AWS follows a pay-as-you-go model with three main cost drivers:

1. **Compute** — time your instances/functions run
2. **Storage** — amount of data stored
3. **Data Transfer** — data OUT of AWS to the internet (data IN is free)

**Cost optimization tips:**
- Use the **AWS Pricing Calculator** (calculator.aws) to estimate costs before deploying
- Right-size your EC2 instances — don't over-provision
- Delete unused resources (snapshots, unattached EBS volumes, idle instances)
- Use S3 lifecycle policies to move data to cheaper storage classes automatically
- Leverage **Reserved Instances** or **Savings Plans** for predictable workloads

---

## 2.9 Quick Reference: AWS Service Categories

| Category | Key Services |
|---|---|
| **Compute** | EC2, Lambda, ECS, EKS, Elastic Beanstalk |
| **Storage** | S3, EBS, EFS, Glacier |
| **Database** | RDS, DynamoDB, ElastiCache, Redshift |
| **Networking** | VPC, Route 53, CloudFront, Direct Connect, API Gateway |
| **Security** | IAM, KMS, Shield, WAF, GuardDuty, Security Hub |
| **Monitoring** | CloudWatch, CloudTrail, Config, X-Ray |
| **Developer Tools** | CodeCommit, CodeBuild, CodeDeploy, CodePipeline |
| **AI/ML** | SageMaker, Rekognition, Comprehend, Bedrock |
| **Management** | Organizations, Control Tower, Systems Manager |

---

*Previous: [Chapter 1 — Creation of AWS Account](./01-creation-of-aws-account.md)*  
*Next: [Chapter 3 — AWS SBG (dbit)](./03-aws-sbg-dbit.md)*
