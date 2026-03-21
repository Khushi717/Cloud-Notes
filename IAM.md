
# IAM(Identity and access Management)

AWS Identity and Access Management (IAM) is a security service that **controls who can access AWS resources and what actions they can perform**. IAM helps manage **users, permissions, and authentication** securely. Helps you to secure AWS service that helps you control access to AWS resources. Help you manage what to do in your AWS cloud account. 

```jsx
	User → IAM → AWS Resources (EC2, S3, RDS)
```

# Purpose of IAM

IAM provides two main security mechanisms.

## 1. Authentication

Authentication answers:

```
Who is trying to access AWS?
```

Examples:

1. IAM User
2. Application
3. EC2 instance
4. External service

**Authentication methods:**

- Username and password
- Access keys
- Multi-factor authentication (MFA)

---

## 2. Authorization

Authorization answers:

```
What are they allowed to do?
```

Examples:

1. Read S3 bucket
2. Start EC2 instance
3. Delete database

Permissions are defined using **policies**.

---

# Components of IAM

IAM has **five main components**.

#### 1. IAM Users

An **IAM user** represents a person or application that needs access to AWS.

Example:

```
Developer
Admin
Application user
```

Each user can have username, password, access keys

Example:

```
User: Anjali
Permission: Access S3
```

---

#### 2. IAM Groups

An **IAM group** is a collection of users. Manage permissions for multiple users easily

Example:

```
Developers group
Admins group
Testers group
```

If you add a user to the group, they automatically get the group's permissions.

Example:

```
Group: Developers
Permission: EC2 access
Users: Rahul, Anjali, Priya
```

---

# 3. IAM Policies

A **policy** is a JSON document that defines permissions.

Policies answer:

```
What actions are allowed or denied?
```

Example policy:

```
{
 "Effect":"Allow",
 "Action":"s3:ListBucket",
 "Resource":"*"
}
```

Meaning:

```
Allow listing S3 buckets
```

AWS provides **managed policies** like- AmazonS3ReadOnlyAccess, AdministratorAccess, AmazonEC2FullAccess

---

# 4. Permissions

Permissions are the **rules defined by policies**.

They control:

```
Read
Write
Delete
Execute
```

Example:

```
User can read S3 bucket
User cannot delete objects
```

---

# 5. IAM Roles

A **role** is a temporary permission given to AWS services or users.

Roles are commonly used for:

- EC2
- Lambda
- Applications

Example:

```
EC2 Instance → IAM Role → Access S3
```

Instead of storing passwords, EC2 uses temporary credentials.

Benefits:

- more secure
- no hardcoded access keys

# Best Practices for IAM

Important security practices:

1. Enable MFA (multi-factor authentication)
2. Use roles instead of access keys
3. Follow least privilege principle
4. Do not use root account for daily work.

→ Customer responsibility changes based on service you pick

→ AWS Pricing = Compute + Storage + Data OUT
