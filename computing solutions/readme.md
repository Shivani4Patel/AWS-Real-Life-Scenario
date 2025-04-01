# EC2 Instance Type Upgrade Guide

## Overview

This guide provides the necessary steps to change an Amazon EC2 instance to a larger instance type to meet the increasing compute and memory requirements. The example involves upgrading an instance to the `m4.large` type.

---
![image](https://github.com/user-attachments/assets/b1fb156e-046c-4411-8e4f-c297f3a2ccdf)

## Concept

In this practice lab, you will:
- Explore Amazon EC2 instance types.
- Filter EC2 instances based on their attributes.
- Connect to an EC2 instance using Session Manager.
- View EC2 instance metadata by using the instance's public IP address.
- Start and stop an EC2 instance using the Amazon EC2 console.

---

## Goals

- **Explore** Amazon EC2 instance types.
- **Filter** EC2 instances based on their attributes.
- **Connect** to an EC2 instance via Session Manager.
- **View** EC2 instance metadata through the public IP.
- **Start and stop** an EC2 instance using the Amazon EC2 console.

---

## Steps to Change EC2 Instance Type

### Step 1: Confirm Region Selection
1. In the top navigation bar, ensure the **Region** is set to **N. Virginia** (`us-east-1`).
2. In the **Services** search box, type `ec2`.
3. Select **EC2** from the search results.

---

### Step 2: Access EC2 Instances
1. In the left navigation pane, click **Instances**.

---

### Step 3: Select EC2 Instance
1. In the **Instances** section, choose the checkbox to select the **AWS Computing Solutions instance**.
2. On the **Details** tab, review the instance details.

---

### Step 4: Filter Instance Types
1. In the left navigation pane, click **Instance Types**.
2. In the **Instance types** search box, type and press Enter after each:
   - `t3.large`
   - `c5.large`
   - `r5.large`
3. Select the top checkbox to select all three of the filtered instance types.

---

### Step 5: Review Instance Type Details
1. Review the instance type details, including compute, networking, and storage.
2. Scroll down to see the **Pricing details**:
   - Prices vary based on vCPUs, memory, network performance, and other resources.
   - Prices may also vary based on operating systems and their license fees.

---

### Step 6: View Instance Metadata
1. In the **Instances** section, click to select the **AWS Computing Solutions instance**.
2. Under the **Public IPv4 address** on the **Details** tab, click the copy icon to copy the address.

---

### Step 7: Review Instance in Browser
1. Open a new browser tab.
2. Paste the copied IP address in the address bar (ensure to use `http://`, not `https://`).
3. Review the instance details in the browser.

---

### Step 8: Connect to the Instance
1. Return to the Amazon EC2 console tab.
2. In the **Instances** section, click **Connect**.
3. Review the connection settings and choose the **Session Manager** tab.

---

### Step 9: Open Session Manager
1. Click **Connect** in the Session Manager tab to open a new browser tab with the command-line shell.

---

### Step 10: Root Privileges and Navigation
1. To provide root privileges, run the following command:
   ```bash
   sudo -i
To change to the application directory, run:
cd ../home/ec2-user/sample_app
To view files in the sample application directory, run:
ls
Step 11: Check Logs
To check the instance log, run:
tail -lf aws_compute_solutions.log
Step 12: Stop and Start the Instance
In the Instances section, expand the Instance state dropdown and select Stop instance.
Once the instance state changes to Stopped, select Start instance to restart the instance with the new configuration.
DIY Goal

- Change the Amazon EC2 instance type to a larger instance (e.g., m4.large).




## Additional Information
You are only required to configure the instance type change.
Instance Metadata: By configuring the instance metadata service, instance details like instance ID and type can be viewed via a web browser.
Session Manager: A secure way to manage EC2 instances without needing to open ports, manage SSH keys, or use bastion hosts.
Instance Types: AWS offers multiple instance types tailored for different workloads. Be sure to select one that meets your specific needs for compute, memory, and storage.
Conclusion

Upgrading the EC2 instance type ensures your application runs smoothly by providing the necessary resources to handle compute-heavy tasks. Once you’ve completed the process, verify that the instance is running with the desired configuration and the necessary resources are available.

