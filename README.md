# AWS Handbook

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/9/93/Amazon_Web_Services_Logo.svg" width="120" alt="AWS Logo"/>
</p>

> A comprehensive guide to getting started with Amazon Web Services — from account setup to certification.

---

## About This Handbook

This handbook is designed for engineers, developers, and IT professionals who are new to AWS or looking to build a structured foundation in cloud computing. It walks you through everything you need — from creating your first AWS account, understanding core cloud concepts, working in a sandbox training environment, and navigating the AWS certification landscape.

Maintained by the **AWS Student Builder Group (SBG) at DBIT** in collaboration with the Department of AI & ML, Don Bosco Institute of Technology, Bengaluru.

---

## Table of Contents

| Chapter | Title | Description |
|---|---|---|
| [1](./01-creation-of-aws-account.md) | **Creation of AWS Account** | Step-by-step account setup, MFA, billing alerts, Free Tier, Builder Center signup |
| [2](./02-aws-and-cloud-basics.md) | **AWS & Cloud Basics** | Cloud history, service models, global infrastructure, core services, pricing |
| [3](./03-aws-sbg-dbit.md) | **AWS SBG (dbit)** | Sandbox environment, SSO access, labs with screenshots, community links |
| [4](./04-certifications-and-resources.md) | **Certifications & Resources** | All cert paths including AI Practitioner, free voucher via Builder Center |

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
Everything you need to get your AWS account up and running securely. Covers the 8-step sign-up process with a pre-creation checklist, enabling MFA on the root user, creating an IAM admin user, setting up billing alerts, and understanding the AWS Free Tier. Also includes sign-up for AWS Builder Center (student rewards up to $579) and AWS SBG DBIT community links. Features screenshots of the AWS Console.

### Chapter 2 — AWS & Cloud Basics
A thorough introduction to cloud computing concepts and the AWS platform. Starts with a before/after comparison of traditional vs. cloud infrastructure and an AWS timeline from 2006 to today. Covers cloud deployment models, service models (IaaS/PaaS/SaaS), global infrastructure (Regions, AZs, Edge Locations), the Shared Responsibility Model, a five core services quick-look with service icons, and all AWS services across compute, storage, networking, databases, security, and monitoring.

### Chapter 3 — AWS SBG (dbit)
A practical guide to the internal sandbox training environment. Explains how sandbox accounts are governed within AWS Organizations, how to access them via SSO or IAM (with IAM Dashboard screenshot), what you can and cannot do within the environment, spend controls, and five hands-on labs covering S3, EC2, Lambda, DynamoDB, and VPC — with console screenshots for S3 and EC2 labs. Includes AWS SBG DBIT community links and feedback forms.

### Chapter 4 — About Certifications and Resources
The complete AWS certification roadmap including the new **AI Practitioner (AIF-C01)** — recommended for AIML students. Covers all levels from Foundational through Professional, with a dedicated AIML certification path. Includes a free exam voucher path via AWS Builder Center (earn 21 badges → $100 voucher), exam prep strategy, official and third-party resources, registration steps, and what to do after you pass.

---

## AWS Certification Path at a Glance

```
                    ┌─────────────────────────────┐
                    │   Cloud Practitioner CLF-C02 │  ← Start here
                    └──────────────┬──────────────┘
                                   │
         ┌─────────────────────────┼──────────────────────┐
         ▼                         ▼                      ▼
┌─────────────────┐    ┌──────────────────┐   ┌────────────────────┐
│  AI Practitioner│    │   Solutions      │   │  SysOps Admin      │
│  AIF-C01        │    │   Architect      │   │  Associate         │
│  (AIML path)    │    │   SAA-C03        │   │  SOA-C02           │
└────────┬────────┘    └───────┬──────────┘   └──────────┬─────────┘
         │                     │                          │
         ▼                     ▼                          ▼
┌─────────────────┐    ┌──────────────────┐   ┌────────────────────┐
│  ML Engineer    │    │  Solutions Arch  │   │  DevOps Engineer   │
│  Associate      │    │  Professional    │   │  Professional      │
│  MLA-C01        │    │  SAP-C03         │   │  DOP-C02           │
└────────┬────────┘    └──────────────────┘   └────────────────────┘
         │
         ▼
┌─────────────────┐
│  GenAI Developer│
│  Professional   │
│  AIP-C01 (2026) │
└─────────────────┘
```

---

## AWS SBG DBIT Community

**AWS Student Builder Group (SBG) at DBIT** organises hands-on workshops, connects students with AWS resources, and helps build real cloud skills for internships and placements.

| Platform | Link | Purpose |
|---|---|---|
| 📢 **WhatsApp Channel** | [Join Here](https://whatsapp.com/channel/0029Vb76rEYATRSlFR1mOg2X) | Workshop updates and lab resources |
| 📸 **Instagram** | [@awssbg_dbit](https://www.instagram.com/awssbg_dbit/) | Event highlights and tips |
| 💼 **LinkedIn** | [AWS SBG DBIT](https://www.linkedin.com/company/aws-sbg-dbit/) | Professional community |
| 🤝 **Meetup** | [AWS SBG at DBIT](https://www.meetup.com/aws-sbg-at-don-bosco-institute-of-technology-bangalore/) | Upcoming events |
| 🌐 **Website** | [awsevents.dbit.edu.in](https://awsevents.dbit.edu.in/) | Events and registration |

---

## Key AWS Links

| Resource | URL |
|---|---|
| AWS Console | [console.aws.amazon.com](https://console.aws.amazon.com) |
| AWS Documentation | [docs.aws.amazon.com](https://docs.aws.amazon.com) |
| AWS Free Tier | [aws.amazon.com/free](https://aws.amazon.com/free) |
| **AWS Builder Center** | [builder.aws.com](https://builder.aws.com) — student rewards up to $579 |
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
├── 01-creation-of-aws-account.md      ← Chapter 1: Account setup + Builder Center
├── 02-aws-and-cloud-basics.md         ← Chapter 2: Cloud history + core services
├── 03-aws-sbg-dbit.md                 ← Chapter 3: Sandbox + labs + community
└── 04-certifications-and-resources.md ← Chapter 4: All certs + AIML path + free voucher
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
*Handbook maintained by the AWS SBG DBIT — Don Bosco Institute of Technology, Bengaluru*
