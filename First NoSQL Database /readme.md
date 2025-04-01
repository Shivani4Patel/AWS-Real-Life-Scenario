# First NoSQL Database with Amazon DynamoDB

## Description
The city's leading streaming entertainment service aims to enhance user experience by gathering metadata on customer viewing habits and storing it in a highly scalable and fast NoSQL database. The primary goal is to introduce features such as digital bookmarks to allow users to resume watching from where they left off. 

## Solution Overview
This project demonstrates the creation and management of a NoSQL database using **Amazon DynamoDB** to achieve the following objectives:
- Create a NoSQL database as an **Amazon DynamoDB table**.
- Add records with a **dynamic schema** to the DynamoDB table.
- Query the DynamoDB table to retrieve user viewing history.

## Steps to Implement

### 1. Creating a DynamoDB Table
- Navigate to **AWS Management Console** and open **DynamoDB**.
- Create a new table named **UserVideoHistory**.
- Set **Partition key** as `userId` (String) and **Sort key** as `lastDateWatched` (Number).
- Choose **default settings** and create the table.

### 2. Adding Items with Attributes
- Insert a new item with attributes:
  ```json
  { 
    "userId": "12345-abcd-6789", 
    "lastDateWatched": 1740086439, 
    "videoId": "9875-djac-1859", 
    "preferredLanguage": "en-US", 
    "supportedDeviceTypes": ["Amazon Fire TV", "Amazon Fire Tablet"] 
  } 
Add another attribute lastStopTime with a value of 90 (storing viewing time in seconds).
### 3. Querying Data
Use the Query operation to fetch user data based on userId and lastDateWatched.
Use Scan operation to retrieve all records from the table.
DIY Task Solution

Goal: Add a new item with a unique userId and a rating attribute.

## Solution:

- Create a new item with a unique userId.
- Add a new attribute rating with Number data type.
- Add a rating value (e.g., rating: 5).
- Save and validate the item in the DynamoDB console.
- 
## Conclusion

This project successfully demonstrates how to use Amazon DynamoDB to create a scalable and flexible NoSQL database for an entertainment streaming service. By leveraging DynamoDB’s dynamic schema capabilities, metadata can be efficiently stored and queried to improve user experience.
