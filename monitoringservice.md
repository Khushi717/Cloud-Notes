
# AWS Monitoring service

## **1. AWS CloudWatch (Health monitoring service for AWS)**

CloudWatch is a **monitoring and observability service** used to track performance, logs, and events of AWS resources. It can monitor all services like Saas(EC2), Paas(Lambda) and Iaas(Some AWS managed services). Tracking, Monitoring and observability service like S3 requests, EC2 CPU **usage**, Lambda invocations.

- Default retention is customizable. (Time period of history saved).
- Monitors performances in form of Metrics( count, duration, error) and logs(text logs from Lambda/app)
- Log of Cloud watch is saved in CloudWatch only, but cloud trail log is saved inside S3.
- Alarms( send notification if threshold is reached) and Dashboards monitoring
- EC2, Lambda, RDS Monitoring

**SNS(Simple notification service)**

Eg: Set an alarm if CPU consumption usage is >80%  then take an action and send a notification through SNS.

**Lambda(Used for Event triggering)**

Eg: Event triggers as msg when an amount is debited from account the msg is convert into voice.

**Polly**- converts text to voice.

---

#### Key Functions-

#### 1. Monitoring

CloudWatch monitors services like:

- EC2 (CPU usage)
- Lambda (invocations)
- S3 (requests)
- RDS (database performance)

---

### 2. Metrics

Metrics are **numerical data** used to measure performance.

Examples:

```
CPU usage
Request count
Error count
Duration
```

---

### 3. Logs

Logs are **text records of events**.

Examples:

```
Application logs
Lambda logs
System logs
```

CloudWatch logs are stored **inside CloudWatch**.

---

### 4. Retention

CloudWatch allows **custom retention period**.

You can define:

```
How long logs/metrics should be stored
```

---

### 5. Alarms

CloudWatch alarms trigger actions when thresholds are crossed.

Example:

```
If CPU usage > 80%
→ Trigger alert
```

---

### 6. Dashboards

Used to **visualize monitoring data**.

Example:

```
Graphs of CPU usage
Request traffic
Error rates
```

---

#### Example Use Case

```
EC2 CPU usage > 80%
   ↓
CloudWatch Alarm
   ↓
Send notification using SNS
```

---

#### 7. SNS (Simple Notification Service)

Amazon SNS

SNS is a **messaging service** used to send notifications.

Features-

- Sends alerts via:
    - Email
    - SMS
    - HTTP endpoints

Example-

```
CloudWatch Alarm triggered
   ↓
SNS sends notification
```

```
High CPU usage alert sent to email
```

---

#### 8. Lambda (Event Triggering)

AWS Lambda

Lambda is a **serverless compute service** used to run code automatically on events.

Example-

```
Bank transaction occurs
   ↓
Lambda triggered
   ↓
Process message
```

---

#### 9. Polly (Text to Speech)

Amazon Polly

Polly converts **text into speech**.

Example-

```
Transaction message
   ↓
Convert text → voice
```

---

#### 10. CloudWatch with S3

CloudWatch can monitor S3 activity such as:

- GET requests
- POST requests
- error responses

It is used in Data usage monitoring, Traffic analysis.

Example-

```
User requests S3 data
   ↓
CloudWatch tracks:
   - Number of requests
   - Number of failed requests
```

---

#### 11. HTTP Status Codes (Monitoring)

CloudWatch helps track **error rates**.

**Status Code Categories**

| Code | Meaning |
| --- | --- |
| 2xx | Success (request successful) |
| 3xx | Redirection |
| 4xx | Client error (bad request) |
| 5xx | Server error |

#### Error Rate

```
Error Rate = 4xx + 5xx
```

Used to detect:

- failures
- system issues
- abnormal traffic

Example-

```
Sudden spike in traffic
   ↓
Increase in 4xx/5xx errors
   ↓
CloudWatch detects issue
```

---

## **2. AWS CloudTrail**

It is activity monitoring service used for API Activity logs, User Actions Tracking, Audit and Security, Resource deletion and creation.

- Default retention - history is saved upto 90 days.
- It has no alarm system.
- It tracks **who did what in AWS**.

Example- Ec2 security inbound is changed, Someone creates a new IAM user, Someone deleted S3 bucket, login attempt.

We can see-

Username, time, IP address, what action was performed.

#### Key Features

#### 1. API Activity Logging

Records all API calls.

Example:

```
Create EC2
Delete S3 bucket
Modify security group
```

---

#### 2. User Activity Tracking

Tracks:

```
Login attempts
IAM user creation
Permission changes
```

---

#### 3. Audit and Security

Used for:

- auditing
- compliance
- security analysis

---

#### 4. Resource Tracking

Tracks:

```
Resource creation
Resource deletion
Configuration changes
```

---

#### 5. Storage

CloudTrail logs are stored in S3.

---

#### 6. Retention

90 days event history.

---

#### 7. No Alarm System

CloudTrail does **not provide alarms**. It only logs activities.

#### Example Events are-

```
EC2 security group modified
New IAM user created
S3 bucket deleted
Login attempt detected
```

# CloudWatch vs CloudTrail

| Feature | CloudWatch | CloudTrail |
| --- | --- | --- |
| Purpose | Performance monitoring | Activity tracking |
| Data Type | Metrics + Logs | API logs |
| Alerts | Yes (alarms) | No |
| Storage | CloudWatch | S3 |
| Use Case | System performance | Security & auditing |

---

## Practical knowledge for Cloud Trail

**Objective**- Tracking the S3 bucket created.

Bucket event history of the S3 buckets created.

1. Create the cloud trail for tracking the S3 bucket creation and all services.
2. create the S3 bucket 
3. S3 bucket info and creation is available in Cloud trail event history.
4. Logs of Cloud trail is stored in S3 bucket.

Code and Information of S3 bucket creation available in logs and cloud trail event history-

```jsx
{
    "eventVersion": "1.11",
    "userIdentity": {
        "type": "Root",
        "principalId": "032621929154",
        "arn": "arn:aws:iam::032621929154:root",
        "accountId": "032621929154",
        "accessKeyId": "ASIAQPGDLELBAZVJKCI4",
        "sessionContext": {
            "attributes": {
                "creationDate": "2026-03-20T08:46:42Z",
                "mfaAuthenticated": "true"
            }
        }
    },
    "eventTime": "2026-03-20T09:07:45Z",
    "eventSource": "s3.amazonaws.com",
    "eventName": "CreateBucket",
    "awsRegion": "ap-south-1",
    "sourceIPAddress": "59.145.191.138",
    "userAgent": "[Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/146.0.0.0 Safari/537.36]",
    "requestParameters": {
        "CreateBucketConfiguration": {
            "LocationConstraint": "ap-south-1",
            "xmlns": "http://s3.amazonaws.com/doc/2006-03-01/"
        },
        "bucketName": "aws-s3-cs",
        "Host": "aws-s3-cs.s3.ap-south-1.amazonaws.com"
    },
    "responseElements": null,
    "additionalEventData": {
        "SignatureVersion": "SigV4",
        "CipherSuite": "TLS_AES_128_GCM_SHA256",
        "bytesTransferredIn": 192,
        "AuthenticationMethod": "AuthHeader",
        "x-amz-id-2": "7j2AYBEnwWbWd8qeMJg+zeqvWIjD/hgROpEHhi11sjJLGOI5x6m48gFLBPqQ5+TEP8JI8SQOUYg=",
        "bytesTransferredOut": 0
    },
    "requestID": "Z2XAGE8A1PCY3M8H",
    "eventID": "784f50dd-86ed-45d5-bc3a-b90ed0f85132",
    "readOnly": false,
    "eventType": "AwsApiCall",
    "managementEvent": true,
    "recipientAccountId": "032621929154",
    "eventCategory": "Management",
    "tlsDetails": {
        "tlsVersion": "TLSv1.3",
        "cipherSuite": "TLS_AES_128_GCM_SHA256",
        "clientProvidedHostHeader": "aws-s3-cs.s3.ap-south-1.amazonaws.com"
    }
}
```

## 3. CloudFront

CloudFront is a **Content Delivery Network (CDN)** that **delivers content faster to users by using edge locations**.

Instead of fetching data from the main server every time:

```
User → Edge Location → (cached data)
```

This reduces **latency (delay)**.

---

#### Features-

#### 1. Low Latency

Content is delivered from nearest location enabling faster loading.

---

#### 2. Edge Locations

Global network of servers.

Examples- New York, Mumbai, London.

---

#### 3. Caching

Stores frequently accessed content.

Example- Images, Video, Web files.

---

#### 4. Security

- HTTPS support
- AWS Shield (DDoS protection)
- Signed URLs

---

#### Use Cases

1. Website acceleration
2. Video streaming
3. API delivery
4. Static content delivery

---

## 4. AWS CloudShell

AWS CloudShell

CloudShell is a **browser-based CLI (command-line interface)** provided by AWS.

#### Key Features

#### 1. No Installation Required

You don’t need to install AWS CLI, Python, Tools. Everything is pre-installed.

---

#### 2. Pre-Authenticated

You are already logged into AWS. So no need to configure credentials:

```
No access key setup required
```

---

#### 3. Persistent Storage

CloudShell provides 1 GB persistent storage.

---

#### 4. Regional Service

CloudShell works per region like in ap-south-1 (Mumbai) only.

---

#### Example Command

```hcl
aws s3ls
```

This lists all S3 buckets.

---

#### Use Cases

1. Run AWS CLI commands
2. Debug infrastructure
3. Quick testing
4. Automation

---

#### Architecture

```
Browser
   ↓
CloudShell
   ↓
AWS Services
```

---

## 5. AWS Ray

AWS X-Ray is a **debugging and performance analysis service** used to **trace requests through applications**.

X-Ray helps to-

1. debug errors
2. analyze performance
3. track request flow
4. identify bottlenecks