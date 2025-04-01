## 🎮 Auto-Healing and Scaling Applications for Gaming Café 



 
## 📋 Project Description 
Help Rusty Ketchum, the owner of the city's best gaming café, implement an auto-healing server environment and limit EC2 instance provisioning to manage gaming servers efficiently.

![image](https://github.com/user-attachments/assets/97b3c407-c750-4070-9717-e6796dbd1396)

🚩 Objectives: 
## Auto-heal game servers when instances fail. 
Restrict users to a specific number of servers (EC2 instances). 
Schedule scaling for special gaming events (e.g., parties every Tuesday night). 
 
 
## ✅ Solution Overview 
Auto Scaling Group with Launch Template to automate EC2 instance provisioning and replacement. 
Scaling policies to maintain desired instance counts and handle CPU-based scaling. 
Scheduled scaling actions to prepare game servers for weekly gaming events. 
 
 
## ⚙️ Step-by-Step Setup 
1. Create an AMI (Amazon Machine Image) 
- Select existing Game Server EC2 instance. 
- Create an image (AMI) named GameServer. 
2. Create a Launch Template 
- Name: GameServerTemplate 
- AMI: Use GameServer AMI. 
- Instance Type: t3.micro. 
- Key Pair: GameServerKeyPair (RSA, .pem format). 
- Security Group: WebServerSecurityGroup. 
3. Create an Auto Scaling Group 
- Name: RegularCustomerGameServer. 
- Launch Template: GameServerTemplate. 
- VPC & Subnets: Select appropriate VPC (GameServerVPC) and subnets. 
- Desired Capacity: 2 instances. 
- Min Capacity: 2 instances. 
- Max Capacity: 4 instances. 
- Health Check Grace Period: 240 seconds. 
4. Configure Auto Scaling Policy 
- Policy Name: CPU Utilization. 
- Metric: Average CPU utilization. 
- Target Value: 70% CPU. 
5. Set Up Scheduled Scaling (for weekly gaming events) 
- Name: SecondWaveOfRegulars. 
- Desired Capacity: 3 instances. 
- Min: 3 instances. 
- Max: 4 instances. 
- Recurrence: Every Tuesday, 8:00 PM - 1:00 AM. 
 
 
## 🔑 Key Benefits 
- ✅ Auto-Healing: Automatically replaces unhealthy instances. 
- ✅ User Quota Enforcement: Limits number of provisioned instances. 
- ✅ Event-Based Scaling: Automatically adjusts capacity for scheduled events. 
 
 


 ![image](https://github.com/user-attachments/assets/bd8d3a19-5631-4f31-aa09-3d83cb0e7cfd)

 
 
🎯 Goal Recap: 
Action: Scale down to 0 instances. 
When: Daily at 01:00 AM. 
End time: No end time (runs indefinitely). 
Purpose: Automatically stop all game servers when not in use. 
 
 
✅ Step-by-Step Solution: 
1. Go to Auto Scaling Group 
Open AWS EC2 Console. 
In the left navigation pane, click Auto Scaling Groups. 
Select your Auto Scaling Group (e.g., RegularCustomerGameServer). 
 
 
2. Navigate to Scheduled Actions 
Click on the Automatic Scaling tab. 
Scroll down to Scheduled actions section. 
Click Create scheduled action. 
 
 
3. Configure Scheduled Action
   ![image](https://github.com/user-attachments/assets/f03a935d-b2a7-4c10-bb26-0a7f10a05d04)


 
5. Save the Action 
Click Create. 
 
 
🚀 Result: 
✅ Your Auto Scaling group will scale down to zero instances every day at 1:00 AM — meeting the requirement! 
 
 
🔑 Notes: 
- Cron format 0 1 * * * means 1:00 AM UTC daily. Adjust timezone if needed. 
- Since min, max, and desired capacities are set to 0, no instances will be running after this time. 
- You can always verify this under Activity and Scheduled Actions tabs. 
