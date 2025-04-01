# 🐾 Centralized Amazon EFS File System for Pet Modeling Agency

## 🎯 Objective
Deploy a scalable, centralized file system (Amazon EFS) accessible by all branch servers to store and share pet client images and data — with proper access controls and high availability.

---
![image](https://github.com/user-attachments/assets/acaf3280-9822-406e-bda9-bcec916e2e2d)


## ⚙️ Step-by-Step Implementation

### Step 1: Centralized Storage Solution
1. Use **Amazon Elastic File System (Amazon EFS)** to reduce administrative tasks associated with web servers.
2. EFS eliminates the need for each web server to store configuration, image, and log files separately.

### Step 2: Shared Access to EFS
1. After the EFS file system is created, **Amazon EC2 instances** within the same **Virtual Private Cloud (VPC)** can simultaneously access the shared file system.
2. This setup allows dynamic content to be managed and changed quickly.

### Step 3: Create Mount Targets
1. After the file system is active, create a **mount target** in each **Availability Zone (AZ)**.
2. Each mount target provides an IP address for an endpoint that instances use to mount the file system.

### Step 4: Mount the EFS to EC2 Instances
1. The web servers attach the mount target located within their AZ as a local folder on the instance.

### Step 5: Access and Modify Files
1. EC2 instances can now read and write data in the EFS file system as if it were stored locally.
2. Any changes made by an instance will be reflected in all other instances with access to the file system.

### Step 6: Expand Capacity as Needed
1. Additional instances can be added at any time by creating and attaching the mount target in the appropriate AZ.

---

## 🌟 Key Benefits of Amazon EFS

| Feature                        | Benefit                                         |
|--------------------------------|-------------------------------------------------|
| **Centralized storage**        | Shared access across all branches.             |
| **Auto-scaling (Petabyte-level)** | No storage constraints, grows as needed.       |
| **File-level permissions**     | Separate access for VIP vs. regular clients.   |
| **High durability & availability** | 99.999999999% durability, multi-AZ resilience.|
| **Reduced admin overhead**     | No need for per-branch storage management.     |

---

## ⚙️ Deployment Steps

### Step 1: Review EC2 Web Servers
1. Review the **3 existing web servers** and their **Availability Zones** in the EC2 Dashboard.

### Step 2: Create EFS Security Group
1. **Security Group Name**: `PetModels-EFS-1-SG`
2. **Inbound Rule**:
   - Type: **NFS**
   - Source: **Existing Web_Server_SG** (to restrict access)
3. **VPC**: `PetModels VPC`

### Step 3: Create Amazon EFS File System
1. **File System Name**: `PetModels-EFS-1`
2. **VPC**: `PetModels VPC`
3. **Settings**:
   - Disable backups (for simplicity).
   - Lifecycle: None.
   - Throughput: Bursting.
4. **Network Access**:
   - AZ: `us-east-1a`
   - Security Group: `PetModels-EFS-1-SG`

### Step 4: Attach & Mount EFS to Web Servers
1. **Attach** the EFS file system via the EFS console to get the mount command.
2. For each EC2 instance (`WebServer1`, `WebServer2`, `WebServer3`):
   - Run the following commands:
     ```bash
     sudo -i
     sudo yum install -y amazon-efs-utils
     mkdir data
     sudo mount -t efs -o tls fs-xxxxxxx:/ data
     cd data
     sudo bash -c "cat >> efs-1-setup.log"
     # Add log: efs-1 mounted in site A/B/C using the same method
     cat efs-1-setup.log  # Verify
     ```

### Step 5: Add Mount Targets for High Availability
1. Add mount targets for each AZ (e.g., `us-east-1b`, `us-east-1c`).
2. **Security Group**: `PetModels-EFS-1-SG`

---

## DIY Goals
- Mount an EFS endpoint to a third EC2 instance.
- Test that the files are accessible from the EC2 instance.

### Solution 
- Verify that the **Amazon EFS file system** has been launched and mounted to the EC2 instance (`PetModels-C`).
- Ensure that the correct files are added to the file system.
- The third EFS mount target is in `us-east-1c`.

---

## ✅ Final Outcome

- ✔️ **Centralized, shared storage** for client images and data.  
- ✔️ **Auto-scalable and highly available** system.  
- ✔️ **VIP data protection** via file-level permissions.  
- ✔️ **Eliminated storage inconsistencies** across branches.
