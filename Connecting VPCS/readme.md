

# **VPC Peering for Multi-VPC Communication** ☁️🔗

## **Solution Overview** 🌐

The Marketing and Developer EC2 instances need to access the Financial Services server hosted in the Finance department’s VPC. This can be achieved using **VPC Peering**.
![image](https://github.com/user-attachments/assets/24aeb6d4-46c1-491a-80a1-ff6eba0dd3b8)
---

## **Solution Steps** 🛠️

### **Step 1: VPC Creation** 🌍  
- Separate VPCs are created for **Marketing**, **Finance**, and **Development** departments.
- The **Finance VPC** contains the **Financial Services** server, which needs to be accessed by both the **Marketing** and **Developer** VPCs.

### **Step 2: Default Isolation** 🚧  
- By default, VPCs are isolated from each other.
- To allow traffic between VPCs, **VPC Peering** must be established.

### **Step 3: Create a Peering Connection** 🔗  
- A **VPC peering connection** is created between **Marketing VPC** and **Finance VPC**. This connection allows traffic routing between the two using private IP addresses.

### **Step 4: Update Route Tables** 🛣️  
- For the **Marketing VPC**, add a route pointing to the **Finance VPC** via the peering connection.
- Similarly, for the **Finance VPC**, add a route back to the **Marketing VPC**.

### **Step 5: Communication Between Marketing and Finance VPC** 🌐  
- With the peering connection and route tables updated, **Marketing** and **Finance** VPCs can now communicate.

### **Step 6: Create Additional Peering** 🔄  
- A **VPC peering connection** is created between **Finance VPC** and **Developer VPC**.
- Update the route tables for both VPCs to ensure they can route traffic to each other.

### **Step 7: VPC Peering Limitation** ⚠️  
- **Marketing** and **Developer VPCs** cannot directly communicate with each other, even though they share a common connection to the **Finance VPC**.  
- **VPC peering** is **not transitive**, meaning Marketing and Developer resources can only access the Finance resources.

---

## **AWS Console Instructions** 🖥️

### **Step 1: Access VPC Console**  
1. In the AWS Management Console, type "VPC" in the search bar and select **VPC**.
2. Review available VPCs: **Marketing**, **Finance**, and **Developer** VPCs.

### **Step 2: Configure EC2 Instances**  
1. Go to **EC2** dashboard and select **Instances (running)**.
2. Select the **FinanceServer** instance and copy the private IP address.

### **Step 3: Set Up Session Manager for MarketingServer**  
1. Select **MarketingServer** instance, go to **Networking** tab, and click **Connect**.
2. Use **Session Manager** to open a terminal and test the connection to **FinanceServer** using `ping <FinanceServer_IP>` (Expect no connection initially).

### **Step 4: Modify Route Tables**  
1. In the **VPC Dashboard**, go to **Route tables**.
2. Select the **Marketing route table** and add a new route:
   - **Destination**: `172.31.0.0/16` (Finance VPC CIDR).
   - **Target**: Select the **Marketing <> Finance** peering connection.
3. Save changes.

### **Step 5: Accept Peering Connection**  
1. In **Peering Connections**, click on the newly created **Marketing <> Finance** peering connection.
2. Accept the request and confirm the status is **Active**.

### **Step 6: Verify Communication Between VPCs**  
1. In the **MarketingServer** terminal, run the `ping` command again with the **FinanceServer's** private IP.
2. The **ping** should now work, confirming that the VPC peering is successfully established.

---

## **final Goals** 🏁

1. Configure a VPC peering connection between **Developer** and **Finance** VPCs.
2. Verify the **Developer EC2 instance** can communicate with the **FinanceServer EC2 instance**.

---

## **Solution ** ✅

test the communication between the **Developer** EC2 instance and the **FinanceServer** EC2 instance. A successful **ping** command will confirm that VPC peering is active.

---

## **Key Notes** 📝  
- VPC peering **does not support transitive peering**; direct communication between **Marketing** and **Developer VPCs** is not allowed.
- **VPC Peering** does not require VPNs or gateways; it's handled over AWS’s private network.


