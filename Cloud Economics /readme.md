# Cloud Economics ☁️💰

## Description 🌊
The city's surf shop wants a cost estimate for an architecture with variable server resources for its webstore.

## Technical Annotations 🖥️
- Create an estimate using **AWS Pricing Calculator** 💻.
- Calculate the cost of **Amazon EC2 web servers** ⚡.
- Save and share your estimate 🌍.

<img width="706" alt="image" src="https://github.com/user-attachments/assets/e05af39d-71b0-43f1-83df-a27592f023bf" />



## **AWS Pricing Calculator Steps** 🧮

### **Step 1:** Understanding AWS Pricing Calculator 📊
- Model solutions before building them.
- Explore AWS service price points.
- Review calculations behind estimates.

### **Step 2:** Cost Optimization on AWS 💸
- Take control of costs and optimize spending.
- Pay only for resources actually needed.

### **Step 3 - 9:** Scaling and Demand Management 🔄
- Static resources can overburden or be underutilized.
- AWS resources are **elastic**, adjusting to demand.
- Scaling **out** increases resources, scaling **down** reduces them.
- Use **AWS Pricing Calculator** to estimate costs before committing.

---

## **Solution Steps** 🏗️

### **Creating an Estimate** 📝

#### **Step 1 - Access AWS Pricing Calculator** 🌐
1. Open [AWS Pricing Calculator](https://calculator.aws).
2. Click **Create estimate**.

#### **Step 2 - Setup Web Server Group** 🖥️
1. Click **My Estimate**.
2. Click **Create group**.
3. Name the group **Web Servers**.
4. Click **Create group**.

#### **Step 3 - Add EC2 Service** ⚡
1. Click **Add service**.
2. Search for **EC2** and select **Configure**.
3. Set **Description** to *Web Server Estimate*.
4. Choose **US East (N. Virginia)** region.

#### **Step 4 - Configure EC2 Instance** 🛠️
1. Choose **Shared Instances**.
2. Select **Linux** as OS.
3. Set **vCPUs: 2**, **Memory: 4 GiB**.
4. Choose **t3.medium** instance type.

#### **Step 5 - Choose Pricing Options** 💳
1. Select **On-Demand** pricing.
2. Review **Savings Plans** and **Reserved Instances**.
3. Expand **Show calculations** and verify pricing.

#### **Step 6 - Configure Storage & Data Transfer 💾**
1. Select **General Purpose SSD (gp3)** for storage.
2. Set **Storage amount: 10GB**.
3. Set **Snapshot Frequency: Weekly**.
4. Set **Data Transfer From: Internet (Free)**, **To: Internet**.

#### **Step 7 - Finalizing Estimate** ✅
1. Click **Save and add service**.
2. Click **View summary**.
3. Click **Share** and **Copy public link**.

---

## **final steps** 🛠️
- Change EC2 instance type to **t2.micro**.
- Generate a new price estimate URL.
- Click **Share** to generate a new URL.

---

📌 *This guide helps businesses create cost-effective AWS solutions using the AWS Pricing Calculator!* 🚀
