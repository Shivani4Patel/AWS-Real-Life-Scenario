 

 
 
🌴 System Stabilization via Amazon EC2 for Island Resilience 

🎯 Objective 
Quickly deploy a virtual server using Amazon EC2 to temporarily replace a failing computational module critical for stabilizing the island’s systems, ensuring continuous operation until hardware replacement arrives. 
 
🌟 Key Benefits of Amazon EC2 Deployment 
Feature 
Benefit 
On-demand scalable compute 
Instantly available virtual server — no delays. 
High availability 
Ensures stabilization system runs without outages. 
User Data automation 
Auto-configures server (web interface for monitoring). 
Secure VPC networking 
Controlled, isolated environment. 
Persistent storage (EBS) 
Durable disk storage for instance data. 

![image](https://github.com/user-attachments/assets/85299edf-d221-4436-a477-fbab18473bcb)
  
 
⚙️ Step-by-Step Deployment Summary 
1. Preparation & Script Download 
Review Lab Objectives. 
Access S3 bucket to locate user-data.txt script. 
Download and review the script — configures a web server for instance visibility. 
2. Launch EC2 Instance 
Search EC2 in AWS Console and click Launch instance. 
Name instance (e.g., webserver01). 
Select Amazon Linux 2023 AMI. 
Instance Type: t3.micro. 
Skip Key Pair for simplicity (temporary lab scenario). 
VPC & Subnet: Select provided Lab VPC and us-east-1a subnet. 
Security Group: Create Lab-SG allowing HTTP (port 80) traffic. 
Storage: Keep default 8 GiB gp3 volume. 
Attach user-data.txt under Advanced details → User data. 
3. Review & Launch 
Review all settings, click Launch instance. 
Monitor status under View all instances. 
Wait until Running state. 
4. Access the Instance Webpage 
Copy Public IPv4 DNS from instance details. 
Open browser, navigate to http://<Public DNS>. 
Verify instance internal details are displayed — confirms system is live and auto-configured. 
 
 
✅ Final Outcome 
✔️ Virtual compute server active, replacing faulty system temporarily. 
✔️ Web-based monitoring available via public DNS. 
✔️ System resilience ensured until hardware repair is completed. 
✔️ Automated setup using user-data script. 
 
 
🔧 Services Utilized 
Service 
Purpose 
Amazon EC2 
Virtual server for computational needs. 
Amazon EBS 
Persistent storage for instance data. 
Amazon VPC 
Private, secure networking environment. 
Security Groups 
Controls incoming/outgoing traffic. 
Amazon S3 
Storage for user-data script. 
 
 
