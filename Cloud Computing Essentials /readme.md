## Cloud Computing Essentials 
Description: 
The city's web portal team needs a more reliable solution to host their beach wave size prediction webpage. Currently, their on-premise servers are unreliable and difficult to maintain. To improve agility and reliability, the solution involves migrating this static webpage to Amazon S3 with static website hosting. 
 ![image](https://github.com/user-attachments/assets/4c010261-8172-4dd4-8b7e-38802c06bb7b)

 
## Scenario Overview: 
Mayor Jack explains that the city’s beach wave size prediction webpage is critical for residents and tourists but struggles with frequent outages. The IT team confirms that the webpage is static (no server-side scripts), making it a perfect candidate for Amazon S3 static website hosting. 
🌊 Cloud Solution for Beach Wave Prediction Webpage (Amazon S3 Static Hosting) 
🎯 Objective 
Migrate the city's beach wave size prediction webpage from unreliable on-premise servers to Amazon S3 Static Website Hosting, ensuring high availability, scalability, and public access without server maintenance. 
 
 
![image](https://github.com/user-attachments/assets/656b51f6-9dcd-47f7-b4f5-959599e2dd1f)

 
 
⚙️ Deployment Steps 
1. Create and Configure S3 Bucket 
Action: 
Go to AWS Console → S3. 
Create bucket (e.g., website-bucket-xyz). 
Ensure: "Block all public access" is Off. 
2. Upload Website Files 
Content: Upload HTML, CSS, JavaScript files for the webpage. 
Action: 
Rename text.html to error.html for custom error handling. 
3. Set Public Access Permissions 
Bucket Policy: Add JSON policy for public read access: 
json 
CopyEdit 
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
 
4. Enable Static Website Hosting 
Go to: Properties → Static website hosting. 
Settings: 
Enable hosting. 
Index document: index.html. 
Error document: error.html. 
Then rename it to waves.html  
5. Test and Access Website 
Copy S3 Bucket website endpoint URL. 
Test in browser to confirm webpage loads correctly. 
 
 
✅ Final Outcome 
✔️ Reliable & scalable wave prediction webpage. 
✔️ Publicly accessible via S3 static website URL. 
✔️ No server maintenance required — fully managed AWS solution. 
✔️ Resilient to outages, ensuring continuous service for the community. 
 
 
