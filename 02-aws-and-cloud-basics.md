# Chapter 2: AWS & Cloud Basics

---

## 2.1 Before Cloud Computing

Before cloud existed, every company that needed IT infrastructure had to build and manage it themselves.

**What that looked like:**

```
Buy physical servers
        ↓
Set up a data center (space, power, cooling)
        ↓
Hire a team to maintain it 24/7
        ↓
Guess how much capacity you'll need
        ↓
Over-provision (wasted money) or under-provision (system crashes)
        ↓
Pay for all of it whether you use it or not
```

**The real problems this caused:**

| Problem | Impact |
|---|---|
| High upfront cost | A small startup couldn't afford to launch |
| Hard to scale | Getting more capacity took weeks or months |
| Wasted resources | Servers sat idle most of the time |
| Single location | One power cut or flood could take everything down |
| Slow to deploy | New infrastructure took days to set up |

---

## 2.2 What is Cloud Computing?

Cloud computing means getting IT resources — servers, storage, databases, networking — over the internet, and paying only for what you use.

You don't buy hardware. You don't set up data centers. You just open a browser, click a few buttons, and your infrastructure is running in minutes.

```
Traditional IT                    Cloud Computing
──────────────────────────        ──────────────────────────────
Buy servers (weeks to arrive)     Launch a server in 60 seconds
Fixed capacity                    Scale up or down instantly
Pay upfront, use or not           Pay only while it's running
One physical location             Deploy globally in minutes
Your team maintains hardware      Cloud provider handles it all
```

---

## 2.3 A Brief History of AWS

Amazon built AWS because they needed a better way to run their own e-commerce infrastructure. In 2006, they opened it up to the world — and the cloud industry was born.

```
2006  →  AWS launches publicly with S3 (storage) and EC2 (servers)
2010  →  Amazon.com itself migrates entirely to AWS
2014  →  AWS Lambda introduces serverless computing
2017  →  SageMaker and AI/ML services launch
2023  →  Amazon Bedrock launches for Generative AI
Today →  200+ services, used by millions of developers worldwide
```

Today AWS holds over **32% of the global cloud market** — more than any other provider.

---

## 2.4 AWS Global Infrastructure

AWS doesn't run from one place. It's built across the globe so your applications can be fast, reliable, and available anywhere.

### Regions
A **Region** is a physical location in the world where AWS has data centers. Each Region is completely independent.

| Region Code | Location |
|---|---|
| `us-east-1` | US East — N. Virginia (most services launch here first) |
| `ap-south-1` | Asia Pacific — Mumbai (closest for India) |
| `eu-west-1` | Europe — Ireland |
| `ap-southeast-1` | Asia Pacific — Singapore |

> Always use **ap-south-1 (Mumbai)** for your labs — it's the closest region and gives you the lowest latency from India.

### Availability Zones
Each Region has **multiple Availability Zones (AZs)** — separate data centers within the same city, connected by high-speed private fiber. If one AZ goes down, the others keep running. This is how AWS achieves high availability.

```
Region: ap-south-1 (Mumbai)
├── AZ: ap-south-1a
├── AZ: ap-south-1b
└── AZ: ap-south-1c
```

### Edge Locations
AWS has **400+ edge locations** worldwide. These cache content closer to end users so websites and apps load faster. Used by Amazon CloudFront (AWS's CDN).

---

## 2.5 AWS Service Quick Reference

| Category | Key Services |
|---|---|
| **Compute** | EC2, Lambda, ECS, EKS, Elastic Beanstalk |
| **Storage** | S3, EBS, EFS, Glacier |
| **Database** | RDS, DynamoDB, ElastiCache, Redshift |
| **Networking** | VPC, Route 53, CloudFront, API Gateway |
| **Security** | IAM, KMS, GuardDuty, WAF, Shield |
| **Monitoring** | CloudWatch, CloudTrail, AWS Config |
| **AI / ML** | SageMaker, Bedrock, Rekognition, Comprehend |
| **Developer Tools** | CodeBuild, CodeDeploy, CodePipeline |

---

*Previous: [Chapter 1 — Creation of AWS Account](./01-creation-of-aws-account.md)*
*Next: [Chapter 3 — AWS SBG DBIT](./03-aws-sbg-dbit.md)*
