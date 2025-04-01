# 🛠️ AWS Secure Networking Environment for Bank

## 📋 Overview
The bank has migrated its services to AWS but is experiencing connectivity issues between its Amazon EC2 instances and databases. The EC2 instances are unable to connect to the internet, and the databases cannot communicate with the instances. The objective is to review and fix the Virtual Private Cloud (VPC) network configurations to resolve the connectivity issues and establish secure communication between resources within the VPC and the internet.

## 🚀 Solution Approach

To address the connectivity issues, we'll configure the following network components:
- **Internet Gateway**: Allows communication between the VPC and the internet.
- **Route Tables**: Ensures traffic is properly routed between the internet and EC2 instances.
- **Security Groups**: Control inbound and outbound traffic for the web and database servers.

### Key Components:
1. **Amazon VPC**:
   - A logically isolated virtual network within the AWS Cloud.
   - Contains both public and private subnets.

2. **Internet Gateway**:
   - Provides the internet access for EC2 instances in the public subnet.

3. **Route Tables**:
   - Define how network traffic is routed within the VPC and to the internet.
   
4. **Security Groups**:
   - Control the inbound and outbound traffic to resources like the web and database servers.

---

## 🛠️ Implementation Steps

### Step 1: **Confirm Region**
1. On the top navigation bar, ensure the region is set to **N. Virginia (us-east-1)**.
2. In the Services search box, type **EC2** and select it from the results.

### Step 2: **Check EC2 Instance Public IP**
1. In the EC2 dashboard, select **Instances** from the left navigation pane.
2. Choose the **Web Server** instance and note down the **Public IPv4 address**.

### Step 3: **Test Web Server Access**
1. In a new browser tab, paste the **public IP address** of the Web Server.
2. You should encounter a site timeout message. This is expected and means further configuration is needed.

### Step 4: **Review EC2 Instance Networking**
1. With the **Web Server** instance still selected, go to the **Networking** tab.
2. Review the **Public** and **Private IPv4 addresses** for the Web Server.

### Step 5: **Check Subnet and Route Table**
1. Under the **Subnet ID** section, click the provided ID to open the **Amazon VPC** console.
2. In the **Subnets** section, select the subnet starting with **network-concepts**.
3. Click the **Route table** tab and select the route table that starts with **web-server-netSubnet1**.

### Step 6: **Edit Route Table**
1. Under the **Routes** tab, check the current routing.
2. Click **Edit routes** to modify the existing routes.
3. Remove any existing **NAT Gateway** routes by clicking **Remove**.
4. Add a new route for **0.0.0.0/0** and select **Internet Gateway** as the target.
5. Save the changes.

### Step 7: **Confirm Internet Gateway Association**
1. After editing, verify that the route table now points to the **Internet Gateway** for outgoing traffic.

### Step 8: **Update Web Server Security Group**
1. In the EC2 dashboard, under **Instances**, select the **Web Server** instance.
2. Go to the **Security** tab and click on the **WebServerSecurityGroup**.
3. In the **Inbound rules**, click **Edit inbound rules**.
4. Add a new rule for **HTTP** (port 80) and set the source to **Anywhere-IPv4**.
5. Save the rules.

### Step 9: **Review Outbound Rules**
1. Under **Outbound rules**, ensure there's a rule allowing traffic on port **3306** (for MySQL/Aurora).
2. If missing, click **Edit outbound rules** and add a rule for **All traffic** with destination **0.0.0.0/0**.

### Step 10: **Test Connectivity**
1. Return to the **EC2 Instances** page and select the **Web Server** instance again.
2. Copy the **Public IPv4 address** and paste it in a new browser tab.
3. Ensure the web page loads successfully. The connection from the internet to the web server should be successful.

---

## 🏁 Conclusion

After completing the above steps, the Web Server will be able to access the internet and serve content. Additionally, communication between the Web Server and DB server should be possible once the next set of security group changes are made to allow traffic on port 3306.

---

## 🧰 DIY Goals

1. **Change the Security Group Rules**:
   - Update the security group for the **DB Server** to allow incoming traffic on port **3306** from the **Web Server**.

---

## 🔒 Solution Validation Method

To verify the solution:
- Check the connection from the **Web Server** (located in subnet 10.10

