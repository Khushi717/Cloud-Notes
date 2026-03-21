# Amazon EC2 (Elastic Compute Cloud)

Amazon EC2 is a cloud computing service that provides **resizable virtual servers (instances)** in the cloud. EC2 allows users to run applications without owning physical servers. It belongs to the **Infrastructure as a Service (IaaS)** model.

Conceptually-

```
Your laptop
   ↓
Virtual server in AWS data center
```

So EC2 is basically **a computer running inside an AWS data center**.

---

# Why EC2 is Called “Elastic” ?

The word **elastic** means **scalable or flexible**.

You can:

1. increase CPU
2. increase memory
3. add storage
4. launch multiple servers

Example:

```
1 server → 100 servers during high traffic
```

Then reduce again when demand decreases.

---

# EC2 Architecture

EC2 instances run inside AWS infrastructure:

```
AWS Region
   ↓
Availability Zone
   ↓
VPC (Virtual Private Cloud)
   ↓
EC2 Instance
```

where-

- Region → geographic location
- Availability Zone → data center
- VPC → private network
- EC2 → virtual server

---

# Key Features of EC2

EC2 provides four major computing resources.

### 1. Compute Power

CPU performs calculations and processing.

Example uses:

1. web servers
2. machine learning
3. data processing

---

### 2. Memory (RAM)

RAM stores temporary data for running applications.

Examples:

1. databases
2. caching systems
3. analytics processing

More RAM → better performance for large applications.

---

### 3. Storage

EC2 uses two main storage options.

1. EBS volumes
2. Instance store

Storage stores- Operating system, Application files, Logs, Databases.

---

### 4. Networking

Networking allows communication with other systems.

EC2 provides-

1. public IP
2. private IP
3. security groups
4. load balancing

Important for- 

1. APIs
2. distributed systems
3. streaming

---

# EC2 Instance

An **EC2 instance** is a running virtual machine.

Example:

```
Ubuntu server running in AWS
```

You can perform actions like:

1. start
2. stop
3. reboot
4. terminate

---

# Instance Lifecycle

EC2 instance passes through several states.

```
Pending
Running
Stopping
Stopped
Terminated
```

Where-

- Running → instance active
- Stopped → instance paused
- Terminated → instance deleted

---

# EC2 Instance Types

Instance type defines **hardware configuration**.

It determines:

- CPU
- RAM
- storage
- networking performance

Example instance type:

```
t2.micro
```

Structure:

```
Family + Generation + Size
```

Example:

```
c7g.large
```

Explanation:

- c → compute optimized
- 7 → generation
- large → size

---

# Categories of EC2 Instance Types

AWS provides different instance families for different workloads.

#### 1 General Purpose Instances

Balanced CPU and memory.

Used for-

1. web servers
2. applications
3. small databases

Examples-

```
T2
T3
M5
```

---

#### 2 Compute Optimized

High CPU performance.

Used for-

1. data processing
2. scientific simulations
3. gaming servers

Examples-

```
C5
C6
```

---

#### 3 Memory Optimized

High RAM.

Used for-

1. large databases
2. analytics
3. in-memory caching

Examples:

```
R5
X1
Z1
```

---

#### 4 Storage Optimized

High disk throughput.

Used for-

1. big data
2. data warehouses
3. NoSQL databases

Examples:

```
I3
D2
H1
```

---

#### 5 Accelerated Computing (GPU)

Used for GPU workloads.

Examples-

1. machine learning
2. video rendering
3. graphics processing

Examples-

```
P2
G3
F1
```

---

# Amazon Machine Image (AMI)

An **AMI (Amazon Machine Image)** is a blueprint used to create EC2 instances. AMI is like a **template of a server**. AMI creates multiple EC2 instances

AMI contains-

1. operating system
2. software
3. configuration
4. permissions

Example:

```
Ubuntu + Apache + Node.js
```

# Types of AMI

#### 1 AWS Provided AMI

Maintained by AWS.

Examples-

1. Amazon Linux
2. Ubuntu
3. Windows Server

---

#### 2 AWS Marketplace AMI

Provided by third-party vendors. Marketplace works like an **app store for server images**.

Examples-

1. WordPress server
2. Jenkins server
3. Database servers

---

#### 3 Custom AMI

Users can create their own AMI.

Example-

```
Company server with preinstalled software
```

Benefits-

1. faster deployment
2. consistent environment

---

# Amazon EBS (Elastic Block Store)

Amazon Elastic Block Store provides **persistent block storage for EC2 instances**.

EBS works like a **virtual hard disk** attached to an EC2 instance.

Example:

```
EC2 Instance
   ↓
EBS Volume
```

---

#### Features of EBS

1. Persistent storage
2. Detachable volumes
3. Snapshot backup
4. High performance

Example usecases:

```
Store OS
Store application data
Store databases
```

---

# Instance Store vs EBS

| Feature | EBS | Instance Store |
| --- | --- | --- |
| Persistence | Data survives reboot | Data lost when instance stops |
| Storage type | Network storage | Local storage |
| Use case | Databases | Temporary data |

---

# EC2 Security

EC2 security is controlled using:

1. Security groups
2. Key pairs
3. IAM roles

---

## Key Pair

Key pairs provide secure login to EC2.

They consist of-

```
Public Key (stored in AWS)
Private Key (.pem file)
```

Example login-

```kotlin
ssh-i key.pem ubuntu@ip-address
```

---

### EC2 Architecture

Typical cloud application architecture:

```
User
 ↓
Internet
 ↓
Load Balancer
 ↓
EC2 Instances
 ↓
Database
 ↓
S3 Storage
```

---

# Advantages of EC2

1. scalable computing
2. pay-as-you-go pricing
3. global infrastructure
4. high availability
5. flexible instance types

---

# Key Pair

When logging into your EC2, AWS uses a key pair.

Types-

1 Public Key

2 Private Key
