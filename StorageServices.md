
## AWS Storage Service

1. **Object Storage**- Amazon S3 (for photo, audio or any unstructured data storage). Storing images, backups, unstructured  ( Google drive/ Dropbox), Global instance. Automatically moving old files to new place.
2.  **Block storage**- Used with EC2 ( looks like hard drive).Running database storing OS, high            performance workloads  (Computer hard disk), Single instance
3. **Amazon EFS-** Shared file systems. Multiple servers need shared files, Distributed Applications, Analytics or ML (Shared office network drive), Multiple instance

---

## Amazon EBS (Block storage for EC2)

It has Low-latency storage for databases transactions and high performance database. It is is a block level storage using EC2. It behaves like a hard disk attached to a server.

**For recovery, snapshot and restoring.**

Backup→ EBS Snapshots

EBS is optimized for-

1. Low latency
2. 2. High performance
3. persistent disk storage for servers

→ EC2 is regional service.

```kotlin
EC2 Instance → EBS volume → attached to EC2 → Snapshot stored in S3 → copied to another region → stored a new EBS volume.
```

```kotlin
EC2 Instance → EBS volume → EBS Volume → EBS Snapshot stored in S3 → Restored EBS Volume→ EC2 instance( Recovery server)
```

---

## File Storage - Amazon EFS

It is a shared file storage service that allows multiple servers to access the same files simultaneously.

(AZ 1) EC2 Instance—-**Amazon EFS**—-(AZ 2)EC2 Instance

---

# AWS Storage Gateway

Hybrid bridge used to connect on-premises systems (private cloud) and AWS cloud storage.

Provide cloud backup solutions.

It allows organization to store data locally while backing up to cloud.

Hybrid on-premises to cloud storage.

```kotlin
Our local datacenter → AWS gateway → **AWS storage gateway** →  amazon simple storage service → Amazon EBS → Amazon EC2
```

**Types of Gateway-**

1. **File Gateway**
    
    Store files in S3
    
    ```kotlin
    Application → File Gateway -> Amazon S3
    ```
    
2. **Volume Gateway**
    
    Block storage backup.
    
    ```kotlin
    App → Volume Gateway → Amazon S3→ EBS Snapshots
    ```
    
3. **Tape Gateway**
    
    Replace physical tape backup systems
    
    ```kotlin
    Backup software → Tape Gateway → Virtual → Amazon S3 → Amazon Glacier
    ```
    
