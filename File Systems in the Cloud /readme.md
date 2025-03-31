## 🐾 Centralized Amazon EFS File System for Pet Modeling Agency 
🎯 Objective 
Deploy a scalable, centralized file system (Amazon EFS) accessible by all branch servers to store and share pet client images and data — with proper access controls and high availability. 


![image](https://github.com/user-attachments/assets/cf6c7255-eb37-44e5-bf0d-16aea47194bc)

![image](https://github.com/user-attachments/assets/4907c214-5639-4f74-a5bb-55a1b15ea389)


⚙️ Deployment Steps 
1. Review EC2 Web Servers 
  Action: Review 3 existing web servers & their Availability Zones in EC2 Dashboard. 
2. Create EFS Security Group 
  Name: PetModels-EFS-1-SG 
  Inbound Rule: 
  Type: NFS 
  Source: Existing Web_Server_SG (to restrict access). 
  VPC: PetModels VPC 
3. Create Amazon EFS File System 
  Name: PetModels-EFS-1 
  VPC: PetModels VPC 
  Settings: 
  Disable backups (for simplicity). 
  Lifecycle: None. 
  Throughput: Bursting. 
  Network Access: 
  AZ: us-east-1a 
  Security Group: PetModels-EFS-1-SG 
4. Attach & Mount EFS to Web Servers 
  Action: 
  Use Attach option in EFS console to get mount command. 
  On each EC2 instance (WebServer1, 2, 3): 
  sudo -i 
  sudo yum install -y amazon-efs-utils 
  mkdir data 
  sudo mount -t efs -o tls fs-xxxxxxx:/ data 
  cd data 
  sudo bash -c "cat >> efs-1-setup.log" 
  # Add log: efs-1 mounted in site A/B/C using the same method  
  cat efs-1-setup.log  # Verify 
 
5. Add Mount Targets for High Availability 
  Action: 
  Add mount targets for each AZ (e.g., us-east-1b, us-east-1c). 
  Security Group: PetModels-EFS-1-SG 
 
 
✅ Final Outcome 
✔️ Centralized, shared storage for client images and data. 
✔️ Auto-scalable and highly available system. 
✔️ VIP data protection via file-level permissions. 
✔️ Eliminated storage inconsistencies across branches. 
