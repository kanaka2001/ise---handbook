# Chapter 1: Creation of AWS Account

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/9/93/Amazon_Web_Services_Logo.svg" width="120" alt="AWS Logo"/>
</p>

---

## 1.1 Overview

An AWS account is your gateway to Amazon Web Services — it gives you access to 200+ cloud services including compute, storage, networking, databases, machine learning, and more. Creating your account correctly from the start sets the foundation for a secure and well-governed cloud environment.

---

## 1.2 What You Need Before You Start

Before visiting [aws.amazon.com](https://aws.amazon.com), have the following ready:

| Requirement | Details |
|---|---|
| **Email Address** | A valid, accessible email (this becomes your root user login) |
| **Account Name** | A meaningful name (e.g., `yourname-aws-learning`) |
| **Phone Number** | For identity verification via call or SMS |
| **Payment Method** | A valid credit/debit card (AWS charges $1 temporarily to verify, then refunds it) |
| **Address** | Your billing/contact address |

> **Tip:** Use a dedicated email for your AWS account, not a shared inbox. You'll receive billing alerts, security notifications, and account recovery emails here.

### Pre-Creation Checklist

- [ ] Laptop and charger ready
- [ ] Stable internet connection available
- [ ] Valid email address accessible
- [ ] Credit or debit card available (for the $1 temporary verification hold)
- [ ] Phone number ready for SMS/voice verification
- [ ] Do **not** create the account on the day of a workshop — account activation can take up to 24 hours

---

## 1.3 Step-by-Step: Creating Your AWS Account

### Step 1 — Go to the AWS Sign-Up Page

1. Open your browser and navigate to [https://aws.amazon.com](https://aws.amazon.com)
2. Click **"Create an AWS Account"** in the top-right corner

---

### Step 2 — Enter Root User Email and Account Name

1. Enter your **email address** — this will be your root user email
2. Enter an **AWS account name** (e.g., `john-doe-sandbox`)
3. Click **"Verify email address"**
4. AWS sends a **verification code** to your email — enter it to continue

---

### Step 3 — Set a Root User Password

1. Create a **strong password** (minimum 8 characters, mix of uppercase, lowercase, numbers, symbols)
2. Confirm the password
3. Click **Continue**

> **Important:** The root user has unrestricted access to your entire account. Protect this credential carefully and avoid using it for day-to-day operations.

---

### Step 4 — Enter Contact Information

1. Choose account type: **Personal** or **Business**
2. Fill in your full name, phone number, and address
3. Read and accept the **AWS Customer Agreement**
4. Click **Continue**

---

### Step 5 — Add a Payment Method

1. Enter your **credit or debit card** details
2. AWS places a **temporary $1 USD authorization charge** to verify the card — this is refunded automatically
3. Click **Verify and Continue**

---

### Step 6 — Identity Verification

1. Choose verification method: **Text message (SMS)** or **Voice call**
2. Enter your phone number and the security check characters
3. Click **Send SMS** or **Call Me**
4. Enter the **4-digit verification code** you receive
5. Click **Continue**

---

### Step 7 — Choose a Support Plan

AWS offers four support plans:

| Plan | Cost | Best For |
|---|---|---|
| **Basic** | Free | Personal projects, learning |
| **Developer** | $29/month | Development/test environments |
| **Business** | $100/month | Production workloads |
| **Enterprise** | $15,000+/month | Mission-critical workloads |

For learning purposes, select **Basic (Free)** and click **Complete sign up**.

---

### Step 8 — Account Activation

1. After sign-up, AWS activates your account — this can take a **few minutes to 24 hours**
2. You'll receive a **confirmation email** once your account is active
3. Sign in at [https://console.aws.amazon.com](https://console.aws.amazon.com) using your root email and password

---

## 1.4 First Steps After Account Creation

Once your account is active, complete these critical setup steps before doing anything else.

### 1.4.1 Enable Multi-Factor Authentication (MFA) on Root User

MFA adds a second layer of security to your root account.

1. Sign in to the **AWS Management Console**
2. Click your account name (top-right) → **Security credentials**
3. Under **Multi-factor authentication (MFA)**, click **Assign MFA device**
4. Choose **Authenticator app** (e.g., Google Authenticator, Authy)
5. Scan the QR code and enter two consecutive codes to confirm
6. Click **Add MFA**

> **Why this matters:** If someone gets your password, MFA prevents them from accessing your account.

---

### 1.4.2 Create an IAM Admin User (Stop Using Root!)

Never use the root account for everyday tasks. Create an IAM user with admin privileges instead.

1. Navigate to **IAM** service in the console
2. Click **Users** → **Create user**
3. Enter a username (e.g., `admin`)
4. Select **"Provide user access to the AWS Management Console"**
5. Set a password
6. On the **Permissions** screen, choose **"Attach policies directly"**
7. Search for and attach **AdministratorAccess**
8. Complete creation and **save the sign-in URL**

From now on, use this IAM user for all console work.

---

### 1.4.3 Set Up Billing Alerts

Avoid surprise charges by setting up cost alerts.

1. Go to **Billing and Cost Management** (search in the console)
2. Click **Budgets** → **Create a budget**
3. Choose **"Zero spend budget"** (alerts you when any charge occurs) or set a custom monthly limit
4. Enter your email address for notifications
5. Click **Create budget**

> Set a budget of **$0** to get notified the moment any charges begin — ideal for learners using the Free Tier.

---

### 1.4.4 Understand the AWS Free Tier

New AWS accounts include the **Free Tier** for 12 months (some services are always free):

| Type | Description | Example |
|---|---|---|
| **12-Month Free** | Free for first 12 months | 750 hrs/month EC2 t2.micro, 5 GB S3 |
| **Always Free** | Never expires | 1 million Lambda requests/month |
| **Trials** | Short-term free access | 90-day Amazon SageMaker trial |

Monitor your Free Tier usage at: **Billing Console → Free Tier**

---

## 1.5 AWS Builder Center — Sign Up After Account Creation

Once your AWS account is active, signing up on **AWS Builder Center** is the next important step. It is the official community platform for AWS builders, and students unlock significant free rewards just for signing up.

### What is AWS Builder Center?

**[builder.aws.com](https://builder.aws.com)** gives you access to:

| Section | What You Get |
|---|---|
| **Learn** | Structured learning paths, training courses, and tutorials |
| **Build** | Hands-on labs and project guides |
| **Community** | Connect with builders globally, publish articles, join discussions |
| **Toolbox** | SDKs, developer tools, and resources |

> No credit card needed. AWS Builder Center uses a separate **AWS Builder ID** — not your AWS Console account credentials.

### Student Rewards — Up to $579 in Value

| Step | Action | Reward |
|---|---|---|
| **Step 1** | Sign up + verify student status via SheerID | 1 year Premium AWS Skill Builder access (**$449 value, free**) |
| **Step 2** | Complete your profile (photo + about section) | Profile badge |
| **7 badges** | Publish articles, comment, stay active | **$10** in AWS credits |
| **14 badges** | Continue engaging with the community | Additional **$20** in AWS credits |
| **21 badges** | Keep building your community presence | AWS Foundational Certification exam voucher (**$100 value**) |

**Sign up using this link:** [https://bit.ly/450cFtS](https://bit.ly/450cFtS)

<p align="center">
  <img src="https://raw.githubusercontent.com/kanaka2001/AIML-workshop/main/workshop-resources/images/qr-builder-center.png" width="200" alt="AWS Builder Center QR Code"/>
  <br/>
  <em>Scan this QR code with your phone camera to open the sign-up page directly</em>
</p>

### Also Explore: AWS Skill Builder

Your Premium Skill Builder access (unlocked after student verification) includes:
- Free digital training courses for every AWS service
- Official certification exam prep courses and practice questions
- Hands-on labs in a real AWS environment — no setup needed
- Role-based learning paths (Cloud Architect, Developer, MLOps, and more)

**Access at:** [skillbuilder.aws](https://skillbuilder.aws) — sign in with your AWS Builder ID

---

## 1.6 Stay Connected — AWS SBG DBIT Community

AWS Student Builder Group (SBG) at DBIT is a student-driven cloud community running in collaboration with the Department of AI & ML. Join these channels to stay updated on workshops, resources, and certification events:

| Platform | Link | Purpose |
|---|---|---|
| 📢 **WhatsApp Channel** | [Join Here](https://whatsapp.com/channel/0029Vb76rEYATRSlFR1mOg2X) | Workshop updates and lab resources |
| 📸 **Instagram** | [@awssbg_dbit](https://www.instagram.com/awssbg_dbit/) | Event highlights and tips |
| 💼 **LinkedIn** | [AWS SBG DBIT](https://www.linkedin.com/company/aws-sbg-dbit/) | Professional community and career posts |
| 🤝 **Meetup** | [AWS SBG at DBIT](https://www.meetup.com/aws-sbg-at-don-bosco-institute-of-technology-bangalore/) | Upcoming events calendar |
| 🌐 **Official Website** | [awsevents.dbit.edu.in](https://awsevents.dbit.edu.in/) | Events and registration |

---

## 1.7 AWS Account Security Checklist

Use this checklist every time you set up a new AWS account:

- [ ] Root user email verified
- [ ] Strong root password set
- [ ] MFA enabled on root user
- [ ] Root user is NOT used for daily work
- [ ] IAM admin user created
- [ ] MFA enabled on IAM admin user
- [ ] Billing alerts configured
- [ ] Free Tier usage tracking enabled
- [ ] Default region selected (choose the closest to you)
- [ ] CloudTrail enabled (for audit logging)

---

## 1.8 Understanding the AWS Console

After signing in, you'll land on the **AWS Management Console**:

<p align="center">
  <img src="https://raw.githubusercontent.com/kanaka2001/AIML-workshop/main/workshop-resources/images/aws-console-home.png" width="720" alt="AWS Management Console Home"/>
  <br/>
  <em>AWS Management Console — starting point for every lab and service</em>
</p>

| Element | Description |
|---|---|
| **Search bar** | Find any AWS service by name |
| **Services menu** | Browse all 200+ services by category |
| **Region selector** | Top-right dropdown — always check which region you're in |
| **Account menu** | Access billing, security credentials, and settings |
| **Recently visited** | Quick access to services you've used |

> **Always check your region!** Resources created in one region are not visible in another.

---

## 1.9 Key Concepts Introduced in This Chapter

| Term | Definition |
|---|---|
| **Root User** | The original account owner with full, unrestricted access |
| **IAM** | Identity and Access Management — controls who can do what in AWS |
| **MFA** | Multi-Factor Authentication — requires a second form of verification |
| **Free Tier** | Limited free usage of AWS services for new accounts |
| **AWS Console** | The web-based UI for managing AWS services |
| **Region** | A geographic area containing AWS data centers |

---

*Next: [Chapter 2 — AWS & Cloud Basics](./02-aws-and-cloud-basics.md)*
