# 🌍 Highly Available Web Applications

## 📋 Overview
The travel agency's website experienced significant downtime during a promotional event due to increased traffic and failure of EC2 instances hosted in a single Availability Zone affected by severe storms. The goal is to design and implement a highly available web application architecture that ensures the website remains online and scalable, even during traffic spikes or potential outages in specific Availability Zones.

## 🚀 Solution
We will be leveraging AWS services to create a fault-tolerant, scalable, and highly available architecture for the travel agency's website.

### Key Components:
1. **Amazon EC2 Auto Scaling**: 
   - Automatically scale EC2 instances to meet traffic demand.
   - Distribute instances across multiple Availability Zones to ensure redundancy.

2. **Elastic Load Balancer (ELB)**: 
   - Distribute incoming traffic across multiple EC2 instances, ensuring no single server is overloaded.
   - Attach an Application Load Balancer (ALB) to the EC2 Auto Scaling group to ensure high availability and distribute traffic efficiently.

3. **Amazon Route 53**:
   - Handle DNS management to direct traffic to the appropriate resources, providing seamless access to users globally.

4. **Amazon CloudFront**:
   - Cache static and dynamic content closer to end users, reducing latency and improving the user experience.

5. **Amazon S3**:
   - Store static assets like images and videos, ensuring they are readily available to the website.

6. **Amazon CloudWatch**:
   - Monitor the health of EC2 instances and trigger alarms for automatic scaling when needed.

---

## 🛠️ Implementation Steps

### Step 1: **Set up Auto Scaling Group**
- Create an Auto Scaling group across multiple Availability Zones.
- Attach the group to an Application Load Balancer (ALB) to distribute traffic evenly.

### Step 2: **Configure Load Balancer**
- Set up an Application Load Balancer that will route traffic to healthy EC2 instances in multiple Availability Zones.
  
### Step 3: **Monitor Health with CloudWatch**
- Set up CloudWatch health checks to monitor the health of EC2 instances, triggering scaling actions when instances reach a predefined CPU utilization threshold.

### Step 4: **Configure DNS and Static Assets**
- Use Amazon Route 53 to configure DNS settings.
- Store and serve static content (e.g., images, videos) from Amazon S3.
- Implement CloudFront to reduce latency by caching content at edge locations.

---

## 🔄 Solution Validation

-  Configure the existing Auto Scaling group to include a new EC2 instance in a third Availability Zone.
-  Confirm the deployment of an Application Load Balancer with a minimum of three EC2 instances spread across three Availability Zones. - CloudWatch monitoring is in place to automatically scale the number of EC2 instances based on real-time demand.

---

## 🏁 Conclusion
By implementing this highly available architecture, the travel agency's website will be able to handle sudden spikes in traffic and remain operational even during infrastructure failures. This solution ensures better uptime, scalability, and performance for the users.

---

