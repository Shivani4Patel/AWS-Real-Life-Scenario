# 🌴 System Stabilization via Amazon EC2 for Island Resilience

## 🎯 Objective
The objective is to quickly deploy a virtual server using **Amazon EC2** to temporarily replace a failing computational module critical for stabilizing the island’s systems. This ensures continuous operation until a physical hardware replacement arrives.

---

## 🌟 Key Benefits of Amazon EC2 Deployment

| **Feature**               | **Benefit**                                                                 |
|---------------------------|-----------------------------------------------------------------------------|
| **On-demand scalable compute** | Instantly available virtual server — no delays.                            |
| **High availability**      | Ensures stabilization system runs without outages.                         |
| **User Data automation**   | Auto-configures server (web interface for monitoring).                     |
| **Secure VPC networking**  | Controlled, isolated environment for enhanced security.                    |
| **Persistent storage (EBS)** | Durable disk storage for instance data, ensuring no data loss.           |

---

## ⚙️ Step-by-Step Deployment Summary

### Step 1: **Preparation & Script Download**
1. **Review Lab Objectives** to ensure all requirements are met.
2. **Access the S3 bucket** to locate the `user-data.txt` script that configures the web server.
3. **Download and review the script**: This script auto-configures the server and makes it accessible for monitoring.

### Step 2: **Launch EC2 Instance**
1. **Search EC2** in the AWS Console and click **Launch instance**.
2. **Instance Name**: Name your instance (e.g., `webserver01`).
3. **Amazon Machine Image (AMI)**: Select **Amazon Linux 2023 AMI**.
4. **Instance Type**: Select **t3.micro** (suitable for a lab scenario).
5. **Key Pair**: Skip for simplicity, as this is a temporary setup for the lab.
6. **VPC & Subnet**: Select the provided **Lab VPC** and **us-east-1a** subnet.
7. **Security Group**: Create a new security group (e.g., `Lab-SG`) and allow **HTTP (port 80)** traffic.
8. **Storage**: Keep the default **8 GiB gp3 volume** for storage.
9. **User Data**: Under **Advanced Details → User data**, attach the `user-data.txt` script.

### Step 3: **Review & Launch**
1. **Review all settings** and click **Launch instance**.
2. Monitor the instance status under **View all instances**.
3. Wait until the instance is in the **Running** state.

### Step 4: **Access the Instance Webpage**
1. In the **EC2 dashboard**, go to **Instance Details** and copy the **Public IPv4 DNS**.
2. Open a browser and navigate to `http://<Public DNS>`.
3. Verify that the internal details of the instance are displayed, confirming the system is live and auto-configured.

---

## 🧰 solution Goals

1. **Launch a Second EC2 Instance**: 
   - Deploy a second instance in a different **Availability Zone** (e.g., `us-east-1b`) of the same AWS Region (N. Virginia).
   - Ensure the new instance is in a separate Availability Zone to maintain high availability.

---

## 🔧 Solution  Method

1. two EC2 instances are deployed in **separate Availability Zones** within the **same AWS Region** (N. Virginia).
2.  Ensure the Region is set to **N. Virginia**. If the Region is changed, the DIY will fail.

---

## ✅ Final Outcome

- ✔️ **Virtual compute server** is active, replacing the faulty system temporarily.
- ✔️ **Web-based monitoring** is available via the public DNS.
- ✔️ **System resilience** is ensured until hardware repair is completed.
- ✔️ Automated setup using **user-data script**.

---

## 🔧 Services Utilized

| **Service**          | **Purpose**                                           |
|----------------------|-------------------------------------------------------|
| **Amazon EC2**       | Virtual server for computational needs.               |
| **Amazon EBS**       | Persistent storage for instance data.                 |
| **Amazon VPC**       | Private, secure networking environment.                |
| **Security Groups**  | Controls incoming/outgoing traffic to EC2 instances.  |
| **Amazon S3**        | Storage for the `user-data.txt` script.               |

---


