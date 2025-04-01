# 📊 Optimizing Relational Database Operations with Amazon RDS

## 🏢 Client: Insurance Company — Challenge & Solution Overview

### 🚨 Challenge:
- Database Administrators (DBAs) overloaded with operational tasks (patching, managing infrastructure).
- Need improved availability, performance, and disaster recovery solutions.
![image](https://github.com/user-attachments/assets/570d1457-d2b8-40ec-a636-aa67a240e07a)

---

## ⚙️ Step-by-Step Implementation

### Step 1: Amazon RDS Instance Setup
1. Use **Amazon Relational Database Service (RDS)** to host a customer application database on an RDS instance in a single Availability Zone (AZ).
   
### Step 2: Automating Database Management
1. Amazon RDS is fully managed, eliminating the need for manual database infrastructure provisioning and maintenance.
2. Automates tasks such as backups, database snapshots, and host replacement to reduce administrative burden.

### Step 3: High Availability with Multi-AZ Deployment
1. Deploy the database across multiple AZs for high availability.
2. Amazon RDS synchronously replicates the data from the primary instance to a standby instance in a different AZ.
   
### Step 4: Automatic Failover
1. If a failure is detected in the primary instance, Amazon RDS automatically fails over to the standby instance.
2. Requests are redirected without the need for manual intervention.
   
### Step 5: Seamless Database Operation
1. The **DNS name record** for the DB instance remains the same, allowing the application to resume database operation without manual administrative intervention.

### Step 6: Scale Performance with Read Replicas
1. For read-heavy workloads, create read-only replicas of the DB instance.
2. Offload read queries to replicas, optimizing performance and increasing aggregate read throughput.

---

## 🎯 Challenge Recap:
- DBAs spending excessive time on operational tasks.
- Need improved availability, performance, and disaster recovery solutions.

---

## 🚀 AWS Solutions Recommended:

| Need                        | AWS Solution                        | Benefit                                          |
|-----------------------------|--------------------------------------|--------------------------------------------------|
| Reduce operational tasks    | Amazon RDS                           | Fully managed, handles patching, backups.       |
| Protect against data loss   | Automated Backups                    | Set retention period for backups.               |
| Disaster recovery           | Multi-AZ Deployment                  | High availability with automatic failover.      |
| Handle heavy read traffic   | Read Replicas                        | Offload read queries to replicas.               |
| Easy migration to RDS       | AWS Database Migration Service (DMS) | Smooth migration without downtime.              |

---

## ⚙️ Technical Steps (Simplified)

### Part 1: Create Amazon RDS DB Instance

1. **Search and Access RDS**:  
   - Go to AWS Console.  
   - In the search bar, type "database".  
   - Click **Aurora and RDS**.

2. **Create Database**:  
   - Left panel → **Databases** → **Create database**.  
   - Choose **Standard create**.  
   - Engine: **MariaDB**.  
   - DB Instance Identifier: `my-database`.

3. **Set Credentials**:  
   - Username: `admin`.  
   - Password: `ILoveLearning!123`.  

4. **Configure Instance**:  
   - Class: Burstable → `db.t3.xlarge`.  
   - Storage: `20 GiB`, General Purpose SSD (gp3).  
   - Enable **autoscaling** (up to 1000 GiB).

5. **Enable High Availability**:  
   - Multi-AZ Deployment: **Yes** (Create standby instance).  
   - Network Settings:  
     - VPC: **Default**
