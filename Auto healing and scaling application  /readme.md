# 🎮 Auto-Healing and Scaling Applications for Gaming Café

## 📋 Project Overview
Help Rusty Ketchum, the owner of the city's best gaming café, implement an **auto-healing server environment** and limit EC2 instance provisioning to manage gaming servers efficiently.

---
![image](https://github.com/user-attachments/assets/defaf773-a3df-449b-8c53-a31f293b11c0)


## 🚩 Objectives
- 🔄 **Auto-heal** game servers when instances fail.
- 📊 **Restrict users** to a specific number of servers (EC2 instances).
- 🎉 **Schedule scaling** for special gaming events (e.g., every Tuesday night).

---

## ✅ Solution Overview
- ⚙ **Auto Scaling Group** with Launch Template to automate EC2 instance provisioning and replacement.
- 📈 **Scaling policies** to maintain desired instance counts and handle CPU-based scaling.
- 📅 **Scheduled scaling actions** to prepare game servers for weekly gaming events.

---

## ⚙️ Step-by-Step Setup

### 1️⃣ Create an AMI (Amazon Machine Image)
- Select an existing **Game Server EC2** instance.
- Create an image (**AMI**) named `GameServer`.

### 2️⃣ Create a Launch Template
- **Name**: `GameServerTemplate`
- **AMI**: Use `GameServer AMI`
- **Instance Type**: `t3.micro`
- **Key Pair**: `GameServerKeyPair` (RSA, `.pem` format)
- **Security Group**: `WebServerSecurityGroup`

### 3️⃣ Create an Auto Scaling Group
- **Name**: `RegularCustomerGameServer`
- **Launch Template**: `GameServerTemplate`
- **VPC & Subnets**: Select `GameServerVPC` and appropriate subnets.
- **Desired Capacity**: `2` instances
- **Min Capacity**: `2` instances
- **Max Capacity**: `4` instances
- **Health Check Grace Period**: `240` seconds

### 4️⃣ Configure Auto Scaling Policy
- **Policy Name**: `CPU Utilization`
- **Metric**: `Average CPU utilization`
- **Target Value**: `70% CPU`

### 5️⃣ Set Up Scheduled Scaling (for weekly gaming events)
- **Name**: `SecondWaveOfRegulars`
- **Desired Capacity**: `3` instances
- **Min**: `3` instances
- **Max**: `4` instances
- **Recurrence**: `Every Tuesday, 8:00 PM - 1:00 AM`

---

## 🔑 Key Benefits
✅ **Auto-Healing**: Automatically replaces unhealthy instances.
✅ **User Quota Enforcement**: Limits the number of provisioned instances.
✅ **Event-Based Scaling**: Automatically adjusts capacity for scheduled events.

---

## 🚀 Usage Summary
| Feature               | Configuration                          |
|----------------------|--------------------------------------|
| 🔄 **Auto-Healing**   | Auto Scaling Group with Health Checks |
| 📊 **Provisioning Limit** | Min: 2, Max: 4 instances             |
| 🎉 **Event Auto-Scaling** | Scheduled Action: 3 instances for events |
| 📈 **Performance Scaling** | CPU Target Tracking at 70%         |

---

## 🎯 Goal Recap
- **Action**: Scale down to `0` instances.
- **When**: Daily at `01:00 AM`.
- **End Time**: No end time (runs indefinitely).
- **Purpose**: Automatically stop all game servers when not in use.

---

## ✅ Step-by-Step Solution
### 1️⃣ Go to Auto Scaling Group
- Open **AWS EC2 Console**.
- In the left navigation pane, click **Auto Scaling Groups**.
- Select your **Auto Scaling Group** (e.g., `RegularCustomerGameServer`).

### 2️⃣ Navigate to Scheduled Actions
- Click on the **Automatic Scaling** tab.
- Scroll down to **Scheduled Actions** section.
- Click **Create Scheduled Action**.

### 3️⃣ Configure Scheduled Action
| Field          | Value                          |
|---------------|--------------------------------|
| **Name**      | `ScaleDownToZero`              |
| **Recurrence** | `0 1 * * *` (Cron for 1:00 AM daily) |
| **Desired Capacity** | `0`                    |
| **Min Capacity** | `0`                        |
| **Max Capacity** | `0`                        |
| **Start Time** | Leave empty (optional)        |
| **End Time**   | Leave empty (no end date)     |

### 4️⃣ Save the Action
- Click **Create**.

---

## 🚀 Result
✅ Your **Auto Scaling Group** will scale down to zero instances every day at `1:00 AM`, meeting the requirement!

---

## 🔑 Notes
- **Cron format `0 1 * * *`** means `1:00 AM UTC` daily. Adjust the timezone if needed.
- Since min, max, and desired capacities are set to `0`, no instances will be running after this time.
- You can always verify this under **Activity** and **Scheduled Actions** tabs.

---

📎 [Learn More](https://docs.aws.amazon.com/autoscaling/ec2/userguide/schedule_time.html)
