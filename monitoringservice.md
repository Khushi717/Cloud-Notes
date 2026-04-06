# AWS Monitoring service

## **1. AWS CloudWatch (Health monitoring service for AWS)**

CloudWatch is a **monitoring and observability service** used to track performance, logs, and events of AWS resources. It can monitor all services like Saas(EC2), Paas(Lambda) and Iaas(Some AWS managed services). Tracking, Monitoring and observability service like S3 requests, EC2 CPU **usage**, Lambda invocations.

- Default retention is customizable. (Time period of history saved).
- Monitors performances in form of Metrics( count, duration, error) and logs(text logs from Lambda/app)
- Log of Cloud watch is saved in CloudWatch only, but cloud trail log is saved inside S3.
- Alarms( send notification if threshold is reached) and Dashboards monitoring
- EC2, Lambda, RDS Monitoring

**SNS(Simple notification service)**

Set an alarm if CPU consumption usage is >80%  then take an action and send a notification through SNS.

**Lambda(Used for Event triggering)**

Event triggers as msg when an amount is debited from account the msg is convert into voice.

**Polly**- converts text to voice.

---

#### Key Functions-

#### 1. Monitoring

CloudWatch monitors services like:

- EC2 (CPU usage)
- Lambda (invocations)- Its is a FAAS. It means serverless computing.  We just need to write the code in functions.
- S3 (requests)
- RDS (database performance)

### 2. Metrics

Metrics are **numerical data** used to measure performance.

Examples:

```
CPU usage
Request count
Error count
Duration
```

### 3. Logs

Logs are **text records of events**.

Examples:

```
Application logs
Lambda logs
System logs
```

CloudWatch logs are stored **inside CloudWatch**.

### 4. Retention

CloudWatch allows **custom retention period**.

You can define:

```
How long logs/metrics should be stored
```

### 5. Alarms

CloudWatch alarms trigger actions when thresholds are crossed.

Example:

```
If CPU usage > 80%
→ Trigger alert
```

### 6. Dashboards

Used to **visualize monitoring data**.

Example:

```
Graphs of CPU usage
Request traffic
Error rates
```

#### Example Use Case

```
EC2 CPU usage > 80%
   ↓
CloudWatch Alarm
   ↓
Send notification using SNS
```

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

#### 9. Polly (Text to Speech)

Amazon Polly

Polly converts **text into speech**.

Example-

```
Transaction message
   ↓
Convert text → voice
```

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

#### 2. User Activity Tracking

Tracks:

```
Login attempts
IAM user creation
Permission changes
```

#### 3. Audit and Security

Used for:

- auditing
- compliance
- security analysis

#### 4. Resource Tracking

Tracks:

```
Resource creation
Resource deletion
Configuration changes
```

#### 5. Storage

CloudTrail logs are stored in S3.

#### 6. Retention

90 days event history.

#### 7. No Alarm System

CloudTrail does **not provide alarms**. It only logs activities.

#### Example Events are-

```
EC2 security group modified
New IAM user created
S3 bucket deleted
Login attempt detected
```

---

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

---

## 3. CloudFront

CloudFront is a **Content Delivery Network (CDN)** that **delivers content faster to users by using edge locations**.

Instead of fetching data from the main server every time:

```
User → Edge Location → (cached data)
```

This reduces **latency (delay)**.

#### Features-

#### 1. Low Latency

Content is delivered from nearest location enabling faster loading.

#### 2. Edge Locations

Global network of servers.

Examples- New York, Mumbai, London.

#### 3. Caching

Stores frequently accessed content.

Example- Images, Video, Web files.

#### 4. Security

- HTTPS support
- AWS Shield (DDoS protection)
- Signed URLs

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

#### 2. Pre-Authenticated

You are already logged into AWS. So no need to configure credentials:

```
No access key setup required
```

#### 3. Persistent Storage

CloudShell provides 1 GB persistent storage.

#### 4. Regional Service

CloudShell works per region like in ap-south-1 (Mumbai) only.

#### Example Command

```hcl
aws s3ls
```

This lists all S3 buckets.

#### Use Cases

1. Run AWS CLI commands
2. Debug infrastructure
3. Quick testing
4. Automation

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

---

## AWS Lambda – serverless computing

Lambda is a  function which detects that new file is uploaded in s3 and triggers SNS and FIFQ. Lambda function finds File and its size.

Lambda is a fully managed service. It means serverless computing. 

SNS sends the notification from the publisher(Lambda) to the Subscriber.

We just need to write the code in functions and AWS handles-

- Servers
- Scaling
- Execution

and that’s why it is a **Faas(Function as a Service)**

---

## Amazon SNS

It is a simple notification service. It is a publisher-subscriber messaging system.

#### Key components of SNS

1. **Publisher**
- System that sends message.
- S3 event, cloud Watch, Lambda, Application
1. **Topic**
- A communication channel where messages are sent.
- Multiple subscribers can listen
1. **Subscriber**
- They receive notification.
- Email, SMS, HTTP endpoint, AWS Lambda

```mermaid
graph TD
  A[User uploads file]-->B[Amazon S3 detects New file]-->C[Amazon SNS Topic publishes Notification]-->D[User receives ‘New file uploaded’]
```

---

## Amazon SQS

Queue service that enables decoupled communication between distributed systems. It is a message queue service that helps systems communicate asynchronously. It is temporary storage for message and acts like a digital waiting line.

Advantages of SQS-

- Systems are **decoupled (independent)**
- Messages are stored safely
- Processing can happen later

```mermaid
graph TD
  A[User uploads file]-->B[Message stored in queue]-->C[Consumer reads message]-->D[Message gets processed]
```

#### Types-

1. **Standard Queue**
- It provides max throughput, ensures at least once message delivery but more than one can be     delivered.
- Order sequence may change but processing is very fast.
- Subscription protocols: SQS, Lambda, Data Firehose, HTTP, SMS, email, mobile application endpoints
1. **FIFO(first in first out)**
- One message at a time with exact one processing.
- Message order is guaranteed with no duplicate messaging
- Use cases-  one payment message at a time, order processing

---

## Amazon Event Bridge

It routes our event like application or cloud watch. Amazon Event Bridge is a serverless, fully managed event bus service that simplifies building event-driven applications by connecting AWS services, SaaS applications, and custom systems.

Amazon Event Bridge is a **serverless event bus** that:

- Collects events from different sources
- Filters them using rules
- Routes them to appropriate targets

It enables **event-driven architecture.**

#### Components-

1. **Event Source**- Service or application that generate an event.
    
    Types-
    
    - AWS services:
        - Amazon S3
        - Amazon EC2
        - Amazon CloudWatch
    - Custom apps
    - SaaS apps
2. **Event Bus**- central pipeline where events are received.
    
    Types-
    
    **Default Event Bus**
    
    - Used by AWS services
    
    **Custom Event Bus**
    
    - Used by your own apps
    
    **Partner Event Bus**
    
    - For SaaS integrations
3. **Rule**- condition that filters event. A rule filters events and decides actions

     Example- 

1. No error→ send notification
    
    Error send to lambda or S3
    
2. If file uploaded in S3 AND file size > 1000 bytes
→ trigger action

Types-

1. **Event Pattern Rule**
    
    Filters based on event content
    
2. **Schedule Rule (CRON)**
    
    Runs at specific time
    
3. Target- service that performs action. 
 The **destination where event is sent**

### Common Targets:

| Target | Purpose |
| --- | --- |
| AWS Lambda | Run code |
| Amazon SNS | Send notifications |
| Amazon SQS | Queue processing |
| Amazon S3 | Store data |
| Step Functions | Workflow |

```mermaid
graph TD
    %% Define Nodes
    S3[File Uploaded to S3]
    EventGen[Event Generated]
    EventBus[Event Sent to Event Bus]
    RuleCheck{Rule Checks Condition}
    TargetSend[Sent to Target]
    Action[Target Executes Action]
    NoMatch[Event Ignored]

    %% Define Connections (Edges)
    S3 --> EventGen
    EventGen --> EventBus
    EventBus --> RuleCheck
    RuleCheck -- "If Matched" --> TargetSend
    TargetSend --> Action
    RuleCheck -- "If Not Matched" --> NoMatch
    
```

---

### **Traditional Approach - EC2**

> Traditional computing is a traditional approach in which users have to launch server, choose OS, install runtime(python,Node.js), configure network, handle scaling, handle CPU usage.
> 

If no user→ you still pay.

(Less managed→ fully customizable).

---

## Serverless(Lambda)

> You **don’t manage servers**, you only **write and run code.**
> 

> No Server management.
> 

AWS (cloud provider) handles:

- Infrastructure
- Operating system
- Scaling
- Availability

#### Serverless Architecture

> How Serverless Works?
> 

```mermaid
graph TD
%% Development Phase
subgraph Development [Development & Setup]
A[Write your function code] --> B[Upload to AWS Lambda]
B --> C[Define Trigger / Event]
end

%% Trigger Sources
subgraph Triggers [Event Sources]
D1[S3 Upload]
D2[API Request]
D3[Schedule/Cron]
end

%% Execution Flow
C -.-> D1
C -.-> D2
C -.-> D3

D1 --> E[Event Occurs]
D2 --> E
D3 --> E

E --> F[Lambda runs automatically]
F --> G[Output is generated]

%% Styling
style B fill:#f96,stroke:#333,stroke-width:2px
style F fill:#3498db,stroke:#fff,color:#fff
style G fill:#2ecc71,stroke:#333
```

#### **Features:**

1. **Stateless**- Each execution is **independent.**
- No memory of previous runs
- Fresh environment every time

Since Lambda is stateless, it uses external storage(temporary storage). 

Do not rely on Lambda for permanent storage.

| Storage Type | Used by Lambda? | Purpose |
| --- | --- | --- |
| `/tmp` | Yes | Temporary |
| S3 | Yes | Permanent files |
| DynamoDB | Yes | Database |
| EFS | Yes | Persistent file system |
| EBS | No | Only for EC2 |
1. **No Server Management**- Users don’t Install OS, Manage hardware, Configure scaling rather they only have to focus on code.
2. **Event-Driven**-  Code runs only when triggered.
3. **Pay Per Use**-  Users pay only when function runs or based on execution time, unlike EC2(traditional computing).

**5. Automatic Scaling**- No manual setup needed.

- If 1 request → 1 function
- If 1 million requests → auto scale

---

### Common services used with Lambda

| Combination | Use Case |
| --- | --- |
| S3 + Lambda | File processing |
| API Gateway + Lambda | Backend APIs |
| SNS + Lambda | Notifications |
| SQS + Lambda | Background jobs |
| Event Bridge + Lambda | Event routing |
| DynamoDB + Lambda | Data storage |

---

### **When not to use lambda?**

1. **High GPU preprocessing**
- No native GPU support
- Limited CPU and memory (even with higher memory settings)
- Not optimized for parallel heavy computation
1. **Long run tasks**
- Maximum execution time = **15 minutes**
- Designed for short-lived functions
1. **Stateful Application**
- Lambda is **stateless**
- No guaranteed persistence between executions

```hcl
Example-
Chat sessions with in-memory state
Real-time multiplayer systems
```

> **EC2 and EC2 containers can be used in replacement.**
> 

---

### Practical knowledge for Lambda, SNS, SQS and Email Triggering

Create the SNS topic and click on create topic

[image.png](images/image5.png)

Create subscription and choose the topic created.

For now select protocol as Email with the email address.

![image.png](images/image6.png)

Create the lambda function 

![image.png](images/image7.png)

Add S3 as a trigger in lambda, which ensures if new file or image is uploaded in S3 we are sent a notification(SNS) on email.

Two lambda functions cannot have same trigger configurations.

![image.png](images/image8.png)

For providing permissions to S3 and SNS by lambda, open the role name URL which will navigate to IAM

![image.png](images/image9.png)

Attach policies of SNS and S3 full access so that lambda can be triggered when document is uploaded on s3 and gives us notification through SNS.

![image.png](images/image10.png)

![image.png](images/image11.png)

Write the Lambda function python code and paste the SNS_URL_Topic and click deploy.

![image.png](images/image12.png)

Add file or image to S3 bucket. Following email will be sent.

![image.png](images/image13.png)

Cloud Watch logs can be viewed from the lambda functions in the monitor section.

![image.png](images/image14.png)

installation files-root volume and block storage volume diff between hibernate terminate and stop

---

## AWS X-Ray(Application Doctor)

Aws X-ray is a distributed tracing service used for tracing service. It helps in finding the root cause of the issue in AWS applications. It tracks how a request travels through different components using trace ID.

- Track requests across services
- Analyze performance
- Debug errors in applications
- debug + performance analysis

**When a request flows through multiple services:**
X-Ray tracks the entire journey of that request

```mermaid
graph LR
    User[User]
    APIGW((API Gateway))
    Lambda{AWS Lambda}
    DB[(Amazon DynamoDB)]
    SNS[Amazon SNS]

    User -->|HTTP Request| APIGW
    APIGW -->|Trigger| Lambda
    Lambda -->|Read/Write Data| DB
    Lambda -->|Publish Message| SNS
    
    %% Styling
    style Lambda fill:#f96,stroke:#333,stroke-width:2px
    style DB fill:#3498db,color:#fff
    style SNS fill:#2ecc71,stroke:#333
```

#### **Components-**

1. **API**- Used to send trace data
2. **SDK**- Added in your application code which collects tracing data.
3. **Dashboard**- Visualizes traces and service map
4. **Integrations**- It works in collaboration with:
    - Amazon CloudWatch
    - Service Lens (combined monitoring view)
    - Lambda, EC2, API Gateway

```mermaid
flowchart TD

    %% Main Node
    A["AWS X-Ray: Distributed Tracing"]

    %% Left Section
    A --> B["Granular Data"]
    B --> C["Segments & Subsegments"]
    C --> D["Segments: Service-level data"]
    C --> E["Subsegments: Downstream calls/logic"]

    %% Middle
    A --> F["Trace ID: Unique Request Identifier"]

    %% Right Sections
    A --> G["AWS Integration Service Map"]
    G --> H["Visualizes entire request journey"]

    A --> I["Latency Analysis"]
    I --> J["Measures time taken by app/services"]

    A --> K["Error & Fault Detection"]
    K --> L["Identifies errors & exceptions"]

    %% Styling for bigger text
    classDef big fill:#1f2937,color:#ffffff,stroke:#ffffff,stroke-width:2px,font-size:20px;
    classDef highlight fill:#f97316,color:#ffffff,stroke:#ffffff,stroke-width:2px,font-size:22px;
    classDef green fill:#22c55e,color:#ffffff,stroke:#ffffff,stroke-width:2px,font-size:20px;
    classDef red fill:#ef4444,color:#ffffff,stroke:#ffffff,stroke-width:2px,font-size:20px;

    %% Apply styles
    class A highlight;
    class B,C,D,E,F,I,J big;
    class G,H green;
    class K,L red;

```

---

## Amazon Codeguru

Is an **ML-power service** that automatically reviews code and detects bugs and security issues and provides recommendations to improve code quality and application  performance.  

AI code reviewer + performance expert               

#### CodeGuru Reviewer

It reviews your source code

- Automatically scans your code
- Finds hard to detect bugs
- Detects security vulnerabilities
- Gives recommendation to fix issues.

#### CodeGuru Profiler

Analyzes runtime performance and identifies:

- Slow code
- High CPU usage
- Memory issues

```hcl
Finds function taking too much time
Suggests optimization
```

```mermaid
graph TD
    %% Main Service Header
    CG[#quot;AMAZON CODEGURU: AI CODE REVIEWER#quot;]

    %% Step 1
    A[#quot;STEP 1: PROVIDE SOURCE CODE#quot;]
    A1(Upload code or connect repository)

    %% Step 2
    B[#quot;STEP 2: ML ANALYSIS#quot;]
    B1(CodeGuru scans for bugs & security issues)

    %% Step 3
    C[#quot;STEP 3: RECOMMENDATIONS#quot;]
    C1(AI provides specific fix suggestions)

    %% Step 4
    D[#quot;STEP 4: IMPROVEMENT#quot;]
    D1(Developer updates code quality)

    %% Connections
    CG --- A
    A --> B
    B --> C
    C --> D
    
    %% Detail Links
    A --- A1
    B --- B1
    C --- C1
    D --- D1

    %% High-Visibility Styling
    style CG fill:#f96,stroke:#333,stroke-width:4px,font-size:22px
    style A fill:#3498db,color:#fff,font-weight:bold,font-size:18px
    style B fill:#3498db,color:#fff,font-weight:bold,font-size:18px
    style C fill:#2ecc71,stroke:#333,font-weight:bold,font-size:18px
    style D fill:#f1c40f,stroke:#333,font-weight:bold,font-size:18px
```

| Feature | X-Ray | Amazon Code guru |
| --- | --- | --- |
| Focus | Request tracing | Code quality |
| Use | Debug app flow | Improve code |
| Output | Service map | recommendation |
| Type | Dynamic(Live Request Tracing) | Static(Source Code) and Runtime Profiling |

---

## AWS health Dashboard(HEIDI)

AWS Health Dashboard (*Health Events Intelligent Dashboard and Insights*) is a service that:

- Provides **real-time visibility** into AWS service health
- generate and sends **notifications (events)** about issues
    - Events can be-
        
        > Service issues
        > 
        
        > Scheduled maintenance
        > 
        
        > Account-specific alerts
        > 
- Shows **account-specific impacts**

Incidents that can be maintained by Dashboard are Monitor health, Account alert, Incident awareness, Scheduled changes, Incident response.

![image.png](images/image15.png)

![image.png](images/image16.png)

![image.png](images/image17.png)

![image.png](images/image18.png)

---

## AWS AI Services using Deep Learning(pre-training)

| Service | What is does | Example Use |
| --- | --- | --- |
| Amazon Rekognition | Image/video analysis | Face detection, object recognition |
| Amazon Comprehend | NLP/Text analysis | Sentiment analysis, key phrase extraction |
| Amazon Polly | Text-speech | Read content aloud |
| Amazon Lex | Chatbot Service | Build voice/ chat interface |
| Amazon Transcribe | Speech to text | Convert audio recordings to text |
| Amazon Translate | Language translation | Real time language conversion |