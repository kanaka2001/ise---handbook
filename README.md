# AWS Handbook

> A comprehensive guide to getting started with Amazon Web Services — from account setup to certification.

---

## About This Handbook

This handbook is designed for engineers, developers, and IT professionals who are new to AWS or looking to build a structured foundation in cloud computing. It walks you through everything you need — from creating your first AWS account, understanding core cloud concepts, working in a sandbox training environment, and navigating the AWS certification landscape.

---

## Table of Contents

| Chapter | Title | Description |
|---|---|---|
| [1](./01-creation-of-aws-account.md) | **Creation of AWS Account** | Step-by-step account setup, IAM, MFA, billing alerts, and Free Tier |
| [2](./02-aws-and-cloud-basics.md) | **AWS & Cloud Basics** | Cloud models, global infrastructure, core services, VPC, IAM, pricing |
| [3](./03-aws-sbg-dbit.md) | **AWS SBG (dbit)** | Sandbox environment access, guardrails, hands-on labs, best practices |
| [4](./04-certifications-and-resources.md) | **Certifications & Resources** | Certification paths, exam details, study strategy, and learning resources |

---

## Quick Start

If you're brand new to AWS, follow the chapters in order:

```
Step 1 → Create your AWS account          (Chapter 1)
Step 2 → Learn cloud and AWS fundamentals (Chapter 2)
Step 3 → Practice in the sandbox (dbit)   (Chapter 3)
Step 4 → Plan your certification path     (Chapter 4)
```

If you already have an account and some AWS experience, jump directly to the chapter most relevant to you.

---

## Chapter Summaries

### Chapter 1 — Creation of AWS Account
Everything you need to get your AWS account up and running securely. Covers the 8-step sign-up process, enabling MFA on the root user, creating an IAM admin user, setting up billing alerts, and understanding the AWS Free Tier. Includes a security checklist to complete after every new account creation.

### Chapter 2 — AWS & Cloud Basics
A thorough introduction to cloud computing concepts and the AWS platform. Covers the three cloud service models (IaaS, PaaS, SaaS), AWS global infrastructure (Regions, Availability Zones, Edge Locations), the Shared Responsibility Model, and all core AWS services across compute, storage, networking, databases, security, and monitoring. Also introduces the AWS Well-Architected Framework.

### Chapter 3 — AWS SBG (dbit)
A practical guide to the internal sandbox training environment. Explains how sandbox accounts are governed within AWS Organizations, how to access them via SSO or IAM, what you can and cannot do within the environment, spend controls, and five ready-to-run hands-on labs covering S3, EC2, Lambda, DynamoDB, and VPC.

### Chapter 4 — About Certifications and Resources
The complete AWS certification roadmap from Foundational through Professional and Specialty levels. Includes detailed exam information for each certification, recommended study paths by role, exam preparation strategy, official and third-party resources, registration steps, and what to do after you pass.

---

## AWS Certification Path at a Glance

```
                    ┌─────────────────────────────┐
                    │   Cloud Practitioner CLF-C02 │  ← Start here
                    └──────────────┬──────────────┘
                                   │
            ┌──────────────────────┼──────────────────────┐
            ▼                      ▼                      ▼
    ┌───────────────┐    ┌──────────────────┐   ┌────────────────────┐
    │  Solutions    │    │   Developer      │   │  SysOps Admin      │
    │  Architect    │    │   Associate      │   │  Associate         │
    │  SAA-C03      │    │   DVA-C02        │   │  SOA-C02           │
    └───────┬───────┘    └───────┬──────────┘   └──────────┬─────────┘
            │                    │                          │
            ▼                    └──────────────────────────┘
    ┌───────────────┐                          │
    │  Solutions    │                          ▼
    │  Architect    │             ┌────────────────────────┐
    │  Professional │             │  DevOps Engineer       │
    │  SAP-C03      │             │  Professional DOP-C02  │
    └───────┬───────┘             └────────────────────────┘
            │
            ▼
    ┌───────────────┐
    │  Specialty    │  Security / Networking / Data / ML / GenAI
    └───────────────┘
```

---

## Key AWS Links

| Resource | URL |
|---|---|
| AWS Console | [console.aws.amazon.com](https://console.aws.amazon.com) |
| AWS Documentation | [docs.aws.amazon.com](https://docs.aws.amazon.com) |
| AWS Free Tier | [aws.amazon.com/free](https://aws.amazon.com/free) |
| AWS Skill Builder (Training) | [skillbuilder.aws](https://skillbuilder.aws) |
| AWS Certification Portal | [aws.amazon.com/certification](https://aws.amazon.com/certification) |
| AWS Architecture Center | [aws.amazon.com/architecture](https://aws.amazon.com/architecture) |
| AWS Pricing Calculator | [calculator.aws](https://calculator.aws) |
| AWS Workshops (Hands-on Labs) | [workshops.aws](https://workshops.aws) |
| AWS re:Post (Community) | [repost.aws](https://repost.aws) |
| AWS Well-Architected Tool | Available in the AWS Console |

---

## File Structure

```
aws-handbook/
├── README.md                          ← You are here (Master Index)
├── 01-creation-of-aws-account.md      ← Chapter 1
├── 02-aws-and-cloud-basics.md         ← Chapter 2
├── 03-aws-sbg-dbit.md                 ← Chapter 3
└── 04-certifications-and-resources.md ← Chapter 4
```

---

## Contributing

If you'd like to add content, fix an error, or update a section:
1. Open the relevant chapter file
2. Make your changes
3. Update this README if you add new sections or files
4. Note the date of the update at the bottom of the modified chapter

---

*Last updated: October 2026*  
*Handbook maintained by the dbit Cloud Practice team*
