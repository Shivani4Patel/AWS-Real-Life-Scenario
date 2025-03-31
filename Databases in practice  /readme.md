## 📊 Optimizing Relational Database Operations with Amazon RDS 
🏢 Client: Insurance Company — Challenge & Solution Overview 
🚨 Challenge: 
Database Administrators (DBAs) overloaded with operational tasks (patching, managing infrastructure). 
Need improved availability, performance, and disaster recovery solutions. 

![image](https://github.com/user-attachments/assets/b5acbdd3-833d-4b18-9962-32e60ab2124a)

🎯 Challenge: 
Database Administrators (DBAs) are spending too much time on operational tasks (patching, managing infrastructure). 
Need for improved availability, performance, and disaster recovery. 




![image](https://github.com/user-attachments/assets/57bcf72a-1696-46ea-80f2-b2529affc9eb)



⚙️ Technical Steps (Simplified) 
Part 1: Create Amazon RDS DB Instance 
      Search and Access RDS: 
      Go to AWS Console. 
      In the search bar, type database. 
      Click Aurora and RDS. 
  - Create Database: 
      Left panel → Databases → Create database. 
      Choose Standard create. 
      Engine: MariaDB. 
      DB Instance Identifier: my-database. 
 -  Set Credentials: 
      Username: admin. 
      Password: ILoveLearning!123. 
  - Configure Instance: 
      Class: Burstable → db.t3.xlarge. 
      Storage: 20 GiB, General Purpose SSD (gp3). 
      Enable autoscaling (up to 1000 GiB). 
  - Enable High Availability: 
      Multi-AZ Deployment: Yes (Create standby instance). 
      Network Settings: 
      VPC: Default. 
      Subnet: Default. 
      Public Access: No. 
 -  Disable Extra Monitoring (for this lab): 
    Uncheck Performance Insights and Enhanced Monitoring to avoid permission issues. 
  - Final Settings: 
    Initial DB name: my_database. 
    Review backup and encryption defaults. 
    Maintenance: Disable auto minor version upgrade. 
  Click Create Database. 
 
 
Part 2: Verify Database Creation 
  - Wait 5-10 minutes until status shows Available. 
  - Go to Databases → Click my-database. 
  - Review summary and available actions (like Create read replica). 
 
 
Part 3: Create Read Replica (for Performance Scaling) 
 -  From the my-database Actions menu, choose Create read replica. 
 
 
Part 4: Enable Backups & Multi-AZ (Already Set Above) 
 -  Backups: Set during creation with retention. 
  - Multi-AZ: Enabled during creation for disaster recovery. 
 
 
Part 5: Plan Database Migration (AWS DMS) 
  Access DMS: 
  Search dms in AWS Console. 
  Click Database Migration Service. 
  Explore DMS Options: 
  Click Recommendations → Learn "How it works". 
  Go to Getting started. 
  Review Discover & Assess, Convert, Migrate steps for future migration planning. 
  Than create rds read replica from actions and create read relica  
 
🎯 Outcome: 
✔️ Less DBA overhead via fully managed RDS 
✔️ Data protection through automated backups 
✔️ High availability & disaster recovery (Multi-AZ) 
✔️ Optimized performance with read replicas 
✔️ Seamless future migration using DMS 
- Reduced operational overhead. 
- Automated backups and disaster recovery (Multi-AZ). 
- Improved performance with read replicas. 
- Future-proof migration using AWS DMS. 
 
