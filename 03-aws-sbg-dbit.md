# Chapter 3: AWS SBG (dbit) — Sandbox & Training Environment

---

## 3.1 Overview

The **AWS SBG (Sandbox/Training Environment)** — referred to internally as **dbit** — is a governed, isolated AWS environment designed to provide hands-on learning and experimentation without risk to production systems or unexpected billing surprises.

This chapter covers how the sandbox environment works, how to access and use it effectively, what you can and cannot do within it, and best practices for getting the most out of your sandbox time.

---

## 3.2 What is a Sandbox Environment?

A **sandbox** is a controlled AWS account (or account segment) that provides:

- A **safe space** to experiment with AWS services
- **Isolated boundaries** — no impact on production workloads
- **Spend controls** — budget limits and automatic guardrails prevent runaway costs
- **Pre-configured guardrails** — security policies, SCPs (Service Control Policies), and permission boundaries already in place
- **Time-limited or recyclable** access — accounts may be reset or recycled after use

> Think of the sandbox as a playground where you're free to build, break, and learn — with safety nets in place.

---

## 3.3 Why Use the SBG (dbit) Environment?

| Benefit | Description |
|---|---|
| **Risk-Free Learning** | Mistakes in sandbox don't affect real systems or customers |
| **No Credit Card Needed** | Pre-provisioned accounts — no personal billing |
| **Governed Access** | Permissions are pre-scoped for learning tasks |
| **Team Consistency** | Everyone uses the same baseline environment |
| **Quick Provisioning** | Access granted in minutes, not days |
| **Hands-On Experience** | Real AWS services, not simulators |

---

## 3.4 SBG Environment Architecture

The sandbox environment is typically structured within **AWS Organizations**, which allows centralized governance across multiple accounts.

```
AWS Organizations (Management Account)
└── Sandbox Organizational Unit (OU)
    ├── dbit-sandbox-user-001   ← Individual or team sandbox account
    ├── dbit-sandbox-user-002
    ├── dbit-sandbox-team-A
    └── dbit-sandbox-team-B
```

### Key Governance Components

| Component | Role |
|---|---|
| **AWS Organizations** | Central management of all sandbox accounts |
| **Service Control Policies (SCPs)** | Org-level guardrails that restrict certain actions (e.g., prevent creating resources in restricted regions) |
| **IAM Permission Boundaries** | Limit the maximum permissions a user/role can have |
| **AWS Budgets** | Auto-alert or terminate resources when spend limit is reached |
| **AWS Config Rules** | Ensure resources comply with security/tagging standards |
| **CloudTrail** | All activity logged for audit and review |

---

## 3.5 Accessing Your Sandbox Account

### 3.5.1 SSO / Federated Login

Most sandbox environments use **AWS IAM Identity Center (SSO)** for access. You log in with your corporate credentials rather than a standalone AWS username/password.

**Steps to access:**
1. Navigate to your organization's **SSO portal URL** (provided by your admin)
2. Sign in with your **corporate/dbit credentials**
3. Select the sandbox account assigned to you from the portal
4. Click **Management Console** to launch the AWS Console
5. Or click **Access Keys** to get temporary CLI credentials

---

### 3.5.2 Direct IAM Login (if SSO is not configured)

If using a direct IAM user:
1. Go to the **sign-in URL** provided by your admin (e.g., `https://<account-id>.signin.aws.amazon.com/console`)
2. Enter your **IAM username and password**
3. Complete MFA if required

---

### 3.5.3 AWS CLI Access in Sandbox

After obtaining temporary credentials from SSO:

```bash
# Configure AWS CLI with temporary credentials
aws configure --profile sandbox
# Enter: Access Key ID, Secret Access Key, Session Token, Region

# Verify access
aws sts get-caller-identity --profile sandbox

# Set as default for your session
export AWS_PROFILE=sandbox
```

---

## 3.6 What You Can Do in the Sandbox

The sandbox environment is designed to support a broad range of learning activities:

### ✅ Typical Sandbox Capabilities

| Service Category | Allowed Activities |
|---|---|
| **Compute (EC2)** | Launch instances (limited sizes — t2.micro, t3.micro), create AMIs, set up Auto Scaling |
| **Serverless (Lambda)** | Create and invoke functions, set up triggers, use layers |
| **Storage (S3)** | Create buckets, upload/download objects, configure policies |
| **Networking (VPC)** | Create VPCs, subnets, security groups, route tables |
| **Database (RDS/DynamoDB)** | Launch small DB instances, create tables, run queries |
| **IAM** | Create roles, policies (within permission boundaries) |
| **CloudFormation** | Deploy IaC templates, manage stacks |
| **CloudWatch** | Set up dashboards, alarms, and log groups |
| **API Gateway** | Create and deploy REST/HTTP APIs |
| **SNS / SQS** | Create topics, queues, and subscriptions |

---

## 3.7 Sandbox Restrictions and Guardrails

To protect costs and security, certain actions are restricted in the sandbox:

### ❌ Common Restrictions

| Restriction | Reason |
|---|---|
| Large EC2 instance types (e.g., m5.4xlarge, c5.9xlarge) | Cost control |
| Resources in restricted/non-approved Regions | Governance and data residency |
| Production-grade RDS Multi-AZ deployments | Cost control |
| Creating new IAM users (only roles allowed) | Security governance |
| Modifying CloudTrail or Config settings | Audit integrity |
| Disabling security services (GuardDuty, Security Hub) | Security compliance |
| Exceeding the monthly spend budget | Automatic enforcement |

> **Note:** Attempting a restricted action will return an `Access Denied` or `This action is not permitted by an SCP` error. This is expected — it doesn't mean your credentials are broken.

---

## 3.8 Sandbox Spend Controls

### Budget Limits
Every sandbox account has a **monthly budget cap** (e.g., $50–$200 depending on your organization's policy).

- At **80% of budget**: You receive an email alert
- At **100% of budget**: Another alert is sent; resources may be automatically stopped
- **Account recycling**: When a sandbox lease expires, the account is wiped and re-provisioned for the next user

### Cost-Conscious Habits for Sandbox

Follow these habits to avoid hitting your budget limit:

```
Daily Hygiene Checklist:
[ ] Stop EC2 instances when not in use (don't terminate — just stop)
[ ] Delete unused RDS instances (they charge even when idle)
[ ] Remove unused Elastic IPs (charged when not attached)
[ ] Clean up old EBS snapshots
[ ] Empty and delete unused S3 buckets
[ ] Delete API Gateways and Lambda functions no longer needed
[ ] Check your spend in Billing Console at least weekly
```

---

## 3.9 Common Sandbox Use Cases & Labs

### Lab 1 — Host a Static Website on S3
**Goal:** Deploy a static HTML/CSS website using S3 static website hosting  
**Services:** S3, Route 53 (optional), CloudFront (optional)  
**Estimated Cost:** < $0.01

**Quick steps:**
1. Create an S3 bucket with a globally unique name
2. Enable **Static website hosting** in bucket properties
3. Upload your `index.html` and assets
4. Set bucket policy to allow public read access
5. Access via the S3 website endpoint URL

---

### Lab 2 — Launch and Connect to an EC2 Instance
**Goal:** Launch a Linux EC2 instance and connect via SSH  
**Services:** EC2, VPC, Security Groups  
**Estimated Cost:** Free Tier eligible (t2.micro)

**Quick steps:**
1. Launch a t2.micro Amazon Linux 2 instance
2. Create or select a key pair
3. Configure Security Group: allow SSH (port 22) from your IP
4. Connect: `ssh -i your-key.pem ec2-user@<public-ip>`

---

### Lab 3 — Create a Serverless API
**Goal:** Build a REST API backed by Lambda and API Gateway  
**Services:** Lambda, API Gateway, IAM  
**Estimated Cost:** Free Tier eligible

**Quick steps:**
1. Create a Lambda function (Python/Node.js) that returns JSON
2. Create an API Gateway REST API
3. Create a GET method integrated with your Lambda
4. Deploy the API and test with `curl` or a browser

---

### Lab 4 — Store and Query Data with DynamoDB
**Goal:** Create a DynamoDB table, insert items, and run queries  
**Services:** DynamoDB, IAM  
**Estimated Cost:** Free Tier eligible

**Quick steps:**
1. Create a DynamoDB table with a partition key
2. Insert a few items via the console
3. Run a **Scan** and a **Query** using the console
4. Try AWS CLI: `aws dynamodb scan --table-name <table-name>`

---

### Lab 5 — Build a VPC from Scratch
**Goal:** Create a custom VPC with public and private subnets  
**Services:** VPC, Subnets, Internet Gateway, NAT Gateway, Route Tables  
**Estimated Cost:** Small charge for NAT Gateway (~$0.045/hr)

**Quick steps:**
1. Create VPC with CIDR `10.0.0.0/16`
2. Create public subnet `10.0.1.0/24` and private subnet `10.0.2.0/24`
3. Attach Internet Gateway to VPC
4. Update public subnet route table to route `0.0.0.0/0` → IGW
5. Launch EC2 in public subnet and verify internet access

---

## 3.10 Sandbox Troubleshooting

| Issue | Likely Cause | Solution |
|---|---|---|
| `Access Denied` on resource creation | SCP restriction or insufficient IAM permissions | Check error message — if SCP, contact admin; if IAM, check your role's policies |
| Resources not visible | Wrong region selected | Check the region selector in the top-right corner |
| EC2 connection refused | Security group not configured | Add inbound rule for SSH (22) or RDP (3389) from your IP |
| Budget alert received | Approaching spend limit | Review Billing Console, stop/delete unused resources |
| Sandbox account expired | Lease period ended | Request a new sandbox account from your admin |
| CLI credentials expired | Temporary SSO credentials expire (typically 1–8 hours) | Re-authenticate via SSO portal to get fresh credentials |

---

## 3.11 Sandbox Best Practices

1. **Tag all resources** — use consistent tags like `Owner`, `Project`, `Environment=sandbox` to track what you created
2. **Use CloudFormation or Terraform** — deploy infrastructure as code so you can tear down and rebuild reproducibly
3. **Document your experiments** — keep notes on what you built, what worked, what didn't
4. **Clean up after each session** — delete resources you no longer need
5. **Don't store sensitive data** — sandbox accounts are shared/recycled; never put real credentials, PII, or proprietary data in them
6. **Use the sandbox to practice certification topics** — it's the best complement to any AWS course or study guide

---

## 3.12 Getting Help in the Sandbox Environment

| Resource | How to Access |
|---|---|
| **AWS Documentation** | [docs.aws.amazon.com](https://docs.aws.amazon.com) |
| **AWS Console Help** | Click the **?** icon in any service console |
| **Internal Slack/Teams Channel** | `#aws-sandbox` or `#dbit-cloud` (as configured by your team) |
| **Admin/IT Support** | Raise a ticket for account issues, permission errors, or budget questions |
| **AWS re:Post** | [repost.aws](https://repost.aws) — community Q&A |

---

*Previous: [Chapter 2 — AWS & Cloud Basics](./02-aws-and-cloud-basics.md)*  
*Next: [Chapter 4 — About Certifications and Resources](./04-certifications-and-resources.md)*
