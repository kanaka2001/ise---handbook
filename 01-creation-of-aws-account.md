# Chapter 1: Creation of AWS Account

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/9/93/Amazon_Web_Services_Logo.svg" width="120" alt="AWS Logo"/>
</p>

---

## 1.1 Overview

An AWS account is your entry point to Amazon Web Services. Everything you build on AWS — servers, storage, databases, AI models — lives inside your account. Creating it correctly from the start ensures you stay secure and avoid unexpected charges.

> **For a detailed visual guide with screenshots, follow this document:**
> [AWS Free Tier Account Creation Guide (Google Doc)](https://docs.google.com/document/d/1NL0-PokC71mwcqYCLNTaYR3wPRFTk5X9LuXGrsQhzSk/edit?usp=sharing)

---

## 1.2 What You Need Before You Start

| Requirement | Details |
|---|---|
| **Email address** | A valid email — this becomes your root user login |
| **Account name** | Something meaningful, e.g. `yourname-aws-learning` |
| **Phone number** | For identity verification via SMS or call |
| **Credit/debit card** | AWS places a temporary $1 hold to verify — it is refunded automatically |
| **Address** | Your billing/contact address |

> Do **not** create your account on the day of a workshop. Activation can take up to 24 hours.

---

## 1.3 Step-by-Step: Creating Your AWS Account

> For screenshots of every step, refer to the [detailed guide](https://docs.google.com/document/d/1NL0-PokC71mwcqYCLNTaYR3wPRFTk5X9LuXGrsQhzSk/edit?usp=sharing).

### Step 1 — Go to the AWS Sign-Up Page

1. Open [https://aws.amazon.com](https://aws.amazon.com)
2. Click **"Create an AWS Account"** in the top-right corner

---

### Step 2 — Enter Your Email and Account Name

1. Enter your **email address** — this will be your root user email
2. Enter an **AWS account name**
3. Click **"Verify email address"**
4. AWS sends a **6-digit verification code** to your email — enter it to continue

---

### Step 3 — Set a Root User Password

1. Create a **strong password** (mix of uppercase, lowercase, numbers, and symbols)
2. Confirm the password
3. Click **Continue**

> The root user has unrestricted access to your entire account. Use it only for initial setup — never for day-to-day work.

---

### Step 4 — Enter Contact Information

1. Choose account type: **Personal** or **Business**
2. Fill in your full name, phone number, and address
3. Accept the **AWS Customer Agreement**
4. Click **Continue**

---

### Step 5 — Add a Payment Method

1. Enter your **credit or debit card** details
2. AWS places a **temporary $1 USD hold** to verify the card — this is refunded automatically
3. Click **Verify and Continue**

---

### Step 6 — Verify Your Identity

1. Choose: **Text message (SMS)** or **Voice call**
2. Enter your phone number and complete the CAPTCHA
3. Enter the **verification code** you receive
4. Click **Continue**

---

### Step 7 — Choose a Support Plan

| Plan | Cost | Suitable For |
|---|---|---|
| **Basic** | Free | Learning and personal projects |
| **Developer** | $29/month | Development and testing |
| **Business** | $100/month | Production workloads |
| **Enterprise** | $15,000+/month | Mission-critical systems |

Select **Basic (Free)** and click **Complete sign up**.

---

### Step 8 — Wait for Account Activation

- Activation takes a few minutes to up to 24 hours
- You will receive a **confirmation email** when your account is ready
- Sign in at [https://console.aws.amazon.com](https://console.aws.amazon.com)

<p align="center">
  <img src="https://raw.githubusercontent.com/kanaka2001/AIML-workshop/main/workshop-resources/images/aws-console-home.png" width="720" alt="AWS Management Console"/>
  <br/>
  <em>AWS Management Console — this is where you land after signing in</em>
</p>

---

## 1.4 Immediately After Activation — Do These First

### Enable MFA on the Root User

MFA adds a second layer of security. Even if your password is stolen, no one can log in without your phone.

1. Sign in to the console → click your account name (top-right) → **Security credentials**
2. Under **Multi-factor authentication (MFA)** → click **Assign MFA device**
3. Choose **Authenticator app** (Google Authenticator or Authy)
4. Scan the QR code → enter two consecutive codes → click **Add MFA**

---

### Create an IAM Admin User

Never use the root account for everyday tasks. Create an IAM user instead.

1. Search for **IAM** in the console → click **Users** → **Create user**
2. Enter a username (e.g. `admin`)
3. Enable **"Provide user access to the AWS Management Console"**
4. On permissions, choose **"Attach policies directly"** → attach **AdministratorAccess**
5. Complete creation → **download the credentials CSV** → save the sign-in URL

From now on, use this IAM user — not root — for all console work.

---

### Set Up a Billing Alert

1. Search for **Billing and Cost Management** → click **Budgets** → **Create a budget**
2. Choose **"Zero spend budget"** — you get an email the moment any charge occurs
3. Enter your email → click **Create budget**

---

## 1.5 Account Setup Checklist

- [ ] Email verified and account activated
- [ ] MFA enabled on root user
- [ ] Root user not used for daily work
- [ ] IAM admin user created
- [ ] Credentials CSV downloaded and saved
- [ ] Billing alert configured
- [ ] Closest region selected in the console

---

*Next: [Chapter 2 — AWS & Cloud Basics](./02-aws-and-cloud-basics.md)*
