# Cloud computing

# Amazon Web Services

It is a cloud service from amazon which provides services like **compute power, 
database, storage, applications, and other IT resources via the internet with pay as you go
pricing.** It can used to crate and deploy any type of application in cloud.

## Traditional IT vs Cloud Computing

### 1. Traditional Infrastructure (On-Premise)

Company must manage Physical servers, Storage systems, Cooling, Power, Networking, Maintenance

- Drawbacks:
    1. Very expensive
    2. Hard to scale
    3. Slow deployment

### 2. Cloud Infrastructure

Infrastructure is managed by cloud providers.

```
User
 ↓
Internet
 ↓
Cloud Provider
 ↓
Virtual Servers / Storage / Databases
```

- Benefits:
    1. No hardware maintenance
    2. Highly scalable
    3. Global access
    4. Pay only for usage

---

# Key Characteristics of Cloud Computing

According to NIST there are **5 essential characteristics**.

### 1. On-Demand Self Service

Users can create computing resources without human interaction.

Example:

```
Launch EC2 instance in minutes
```

---

### 2. Broad Network Access

Services are available through internet and accessed via:

1. laptops
2. phones
3. tablets

Example:

```
Laptop → Internet → AWS Server
```

---

### 3. Resource Pooling

Cloud providers pool computing resources and distribute them to multiple users.

This uses **multi-tenant architecture**.

---

### 4. Rapid Elasticity

Resources can scale automatically.

Example:

```
1 server → 100 servers during high traffic
```

---

### 5. Measured Service (Pay-as-you-go)

Users pay only for what they use.

Example:

```
EC2 used for 2 hours → pay only for 2 hours
```

---

# Cloud Service Models

Cloud services are delivered in **three models**.

## 1. IaaS – Infrastructure as a Service

It provides Virtual machines, Storage, Networking.

- User manages:
    1. OS
    2. Applications
    3. Runtime

Example- Amazon EC2

Example architecture:

```
User
 ↓
Application
 ↓
Operating System
 ↓
Virtual Machine
 ↓
Cloud Infrastructure
```

---

## 2. PaaS – Platform as a Service

Cloud provider manages Infrastructure, OS, Runtime environment

User manages Application code

Examples-  AWS Elastic Beanstalk, Heroku

- Languages supported:
    1. Java
    2. Python
    3. Node.js
    4. Ruby
    5. PHP
    6. .NET

---

## 3. SaaS – Software as a Service

Complete applications delivered via internet.

Users only access the software.

Examples- Google Docs, Microsoft Office 365

Examples in enterprises- SAP, Salesforce, Amazon Workspaces

---

## **Shared responsibility model- divide and conquer**

**It works on shared responsibility model- divide and conquer**. Platform, cloud, infrastructure are provided by AWS service cloud provider. Responsibilities like Platform ,cloud, infrastructure management, Patch and version are managed by service provider. Our responsibility is to manage our data, application and work on platform.

AWS and user both share responsibilities:

#### AWS Responsibility:

1. Physical servers
2. Data centers
3. Networking
4. Hardware
5. Infrastructure security

#### User Responsibility:

1. Your data
2. Applications
3. Security settings
4. OS updates (in some cases)

 **AWS manages the cloud, YOU manage what’s inside the cloud**

### Goal-

1. Build scalable applications
2. No need to manage physical servers
3. High availability & fault tolerance
4. Build scalable applications without owning physical servers and data centers.

---

# Security of Cloud vs Security in Cloud

# Security of the Cloud

Managed by AWS.

AWS protects:

1. physical data centers
2. networking
3. servers
4. storage hardware

Example- AWS manages infrastructure security

# Security in the Cloud

Managed by the customer.

Customer manages:

1. IAM permissions
2. data protection
3. application security
4. operating system patches (for EC2)

Example- User manages data and access control

This is called the **Shared Responsibility Model**.

---

# Cloud Deployment Models

There are five deployment models.

# 1. On-Premises

Infrastructure located in company data center.

Example:

```
Company owns servers
```

---

# 2. Public Cloud

Infrastructure owned by cloud providers.

Example- Amazon Web Services

Users share infrastructure.

---

# 3. Private Cloud

Cloud infrastructure dedicated to a single organization.

Used by- banks, government agencies

---

# 4. Hybrid Cloud

Combination of:

```
Private Cloud + Public Cloud
```

Example:

```
Sensitive data → private cloud
Applications → AWS cloud
```

---

# 5. Community Cloud

Infrastructure shared by organizations with similar requirements.

Example- Universities sharing research infrastructure

---

# AWS Pricing Model

AWS pricing depends mainly on:

```
Compute + Storage + Data Transfer
```

---

# 1. Compute Pricing

Example service:

- Amazon EC2

Pricing based on:

- instance type
- usage hours

---

# 2. Storage Pricing

Example:

- Amazon S3

Cost depends on:

```
GB of data stored
```

---

# 3. Data Transfer Pricing

AWS charges when data moves **out of AWS to internet**.

Example:

```
Download files from S3
```

### AWS Pricing model

AWS follows **pay-as-you-go pricing**.

There are three main pricing models.

1. **Shared pricing model (Reserved)**
Users reserve capacity for **1 or 3 years**.
    - lower cost
    - predictable pricing
    - Cheaper long-term
    - Up to 75% cheaper than on-demand
2. **On-demand pricing model- critical situation**

         Pay only for the time resources are used.

- No commitment
- ****Pay per use
- testing
- unpredictable workloads
- EC2 used for 1 hour → pay for 1 hour
1. **Spot instance pricing model**
    
    Unused AWS capacity sold at very low prices.
    
    - Very cheap
    - Can be terminated anytime
    - batch processing
    - data analysis
    - non-critical workloads
    - 90% cheaper than on-demand

# 200+ cloud services EC2(Elastic Cloud computing)

Provides infra like virtual computer. IBM, Oracle,, SAP Microsoft, Google, Mobile Services, Amazon Workspace are SAAS(a fully managed service) which itself works on IAAS.

Java python Ruby, Node.js, PHP .net, IOS, Android are PAAS.

# AWS Global Infrastructure

1. **Region**- A **Region** is a **geographical area** where AWS has multiple data centers.
Example- Asia Pacific (Mumbai), US East (N. Virginia). It helps in Disaster recovery, Data compliance (data stays in a country), Scalability.
2. **Availability Zone**(Data Center)- Make 2 or more than 2 independent availability zones in an area in case one data center’s data is crashed. Easy, high availability, disaster management, balances load.
3. **Edge Locations**(Cloud front)(CDN-Content delivery network)- 
Edge locations are **closer to users and u**sed by **CloudFront (CDN)** to deliver content faster. Edge locations are **NOT for disaster recovery directly.** They are for **speed (performance)**

        Purpose-

- Low latency (fast loading)
- Faster content delivery
- Caching

      Example: New York, Delhi, London

![image.png](image.png)

# Ways to access AWS

There are **four ways to access AWS services**.

---

## 1. AWS Management Console (GUI)

Browser-based interface.

Used for- beginners, manual configuration

Example:

```
Create EC2 instance from browser
```

---

## 2. AWS CLI (Command Line Interface)

Allows interaction using commands through the access key.

Example:

```
aws s3 ls
```

Used for- automation, scripting

![image.png](image%201.png)

---

![image.png](image%202.png)

## 3. AWS SDK (Programmatic Access)

Used to access AWS services through programming languages. We have to download (Imp)SDK we needed is AWSbuto3. Boto3 SDK is needed for programmatically access to AWS- through local code 

Example SDKs:

1. Python → **Boto3**
2. Java
3. Node.js
4. .NET

Example in Python:

```
importboto3
s3=boto3.client('s3')
```

---

## 4. Infrastructure as Code (IaC)

Tools used to automate infrastructure creation.

Examples- AWS CloudFormation, Terraform

---

# Core AWS Service Categories

AWS services are divided into categories.

## 1. Compute

Used to run applications.

Examples:

1. Amazon EC2 – virtual servers
2. AWS Lambda – serverless computing
3. Amazon ECS – container service
4. Amazon EKS – Kubernetes service

---

## 2. Storage

Used to store data.

Examples:

1. Amazon S3 – object storage
2. Amazon EBS – block storage
3. Amazon Glacier – archive storage

---

## 3. Databases

Managed database services.

Examples:

1. Amazon RDS – relational database
2. Amazon DynamoDB – NoSQL database

---

→ In free tier AWS there are some services which are always free , some are paid for 6 months.
