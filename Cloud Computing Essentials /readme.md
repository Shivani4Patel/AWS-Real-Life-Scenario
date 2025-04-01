# 🌊 Cloud Computing Essentials - Beach Wave Prediction Webpage

## 📌 Project Overview
The city's web portal team needs a **more reliable** solution to host their beach wave size prediction webpage. The current **on-premise servers are unreliable** and difficult to maintain. To improve **agility and reliability**, the solution involves **migrating this static webpage to Amazon S3** with static website hosting.

---

## 🎯 Objective
Migrate the city's **beach wave size prediction webpage** to **Amazon S3 Static Website Hosting**, ensuring **high availability, scalability, and public access** without server maintenance.

---

## 🌟 Key Benefits of Amazon S3 Static Website Hosting

| Feature                 | Benefit                                      |
|-------------------------|----------------------------------------------|
| ✅ Fully Managed Storage | No server management, automatic scaling.     |
| 🌍 Static Website Hosting | Direct, fast access to static content.       |
| 🔄 Highly Available      | 99.999999999% durability, multi-AZ resilience. |
| 🌐 Public Access via S3 URL | Easy access for residents and tourists.    |
| 💰 Cost-Effective        | Pay-as-you-go, reduced maintenance costs.    |

---

## ⚙️ Deployment Steps

### 1️⃣ Create and Configure S3 Bucket
- Go to **AWS Console → S3**
- Create a bucket (e.g., `website-bucket-xyz`)
- Ensure **"Block all public access" is Off**

### 2️⃣ Upload Website Files
- Upload **HTML, CSS, JavaScript** files
- Rename `text.html` to `error.html` for custom error handling

### 3️⃣ Set Public Access Permissions
Add the following **JSON policy**:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::website-bucket-xyz/*"
    }
  ]
}
```

### 4️⃣ Enable Static Website Hosting
- Go to **Properties → Static website hosting**
- Enable hosting, set **index.html** as the index document
- Rename it to **waves.html**

### 5️⃣ Test and Access Website
- Copy **S3 Bucket website endpoint URL**
- Test in a browser to confirm the webpage loads correctly

---

## ✅ Final Outcome
✔️ Reliable & scalable wave prediction webpage  
✔️ Publicly accessible via S3 static website URL  
✔️ No server maintenance required — fully managed AWS solution  
✔️ Resilient to outages, ensuring continuous service for the community  

---

🚀 **Now your city's residents and tourists can access real-time wave size predictions effortlessly!**
