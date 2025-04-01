# 👩‍💻 Setting Up IAM for Support Engineering Team — City Stock Exchange

## 🎯 Objective
Establish an IAM user group and user account to ensure consistent, secure, and efficient access for all Support Engineers to AWS Management Console and developer tools, with read-only permissions for EC2 and RDS.

---

## ⚙️ Step-by-Step Implementation

### Step 1: Create IAM User Group — "SupportEngineers"
1. Search for **IAM** in AWS Console.
2. Go to **User groups** → **Create group**.
3. Group name: **SupportEngineers** (case sensitive).
4. Attach Policy: **AmazonEC2ReadOnlyAccess**.
5. Confirm creation of the user group.

### Step 2: Create IAM User — "support-engineer-1"
1. Go to **Users** → **Create user**.
2. User name: **support-engineer-1**.
3. Enable **AWS Management Console access**.
4. Password: **supportPassword!123** (custom, meets complexity requirements).
5. Uncheck "Users must create a new password at next sign-in".
6. Add user to group: **SupportEngineers**.
7. Tag user:
   - Key: `job-title`
   - Value: `Support Engineer`
8. Create user and save sign-in URL for reference (download .csv file if needed).

### Step 3: Review Security Credentials
1. Select user **support-engineer-1**.
2. Go to **Security credentials** tab:
   - Review **MFA (Multi-Factor Authentication)** for added security.
   - Review **Access keys** (for CLI/API access).

### Step 4: Test IAM User Permissions
1. Sign in using the provided console URL in an Incognito/Private Window:
   - User name: `support-engineer-1`.
   - Password: `supportPassword!123`.

### Step 5: Validate Read-Only Access to EC2
1. Search for **EC2** in AWS Console.
2. Select the correct region: **US East (N. Virginia)**.
3. Navigate to **Instances** (running).
4. Attempt to terminate an instance:
   - **Expected Outcome**: Action fails due to read-only permissions — confirms that access is restricted as intended.

---
## ⚙️ Final Changes
- Add **RDSReadOnlyAccess** policy to **SupportEngineers** IAM user group to allow future read-only access to Amazon RDS.

## ✅ Key Goals
- **Centralized user management** through groups.
- **Predefined read-only access** to Amazon EC2 & RDS.
- **Easy onboarding** with console access and custom passwords.
- **Tagging users** for better identity management (e.g., job titles).

---

## 🛡️ Key Concepts & Takeaways

| Feature                      | Purpose & Outcome                                        |
|------------------------------|----------------------------------------------------------|
| **IAM Groups & Policies**     | Centralize permission management, assign at scale.       |
| **AWS Managed Policies**      | Fast, secure way to assign standard permissions.         |
| **Custom User with Console Access** | Easy access for engineers to AWS tools.           |
| **Tags for Users**            | Organized user management and identification.            |
| **Least Privilege Principle** | Only necessary permissions granted (read-only).          |
| **Permission Denial Test**    | Confirm users cannot perform unauthorized actions.       |

---

## 🔧 AWS Services Used

| Service         | Purpose                                                 |
|-----------------|---------------------------------------------------------|
| **IAM**         | Manage users, groups, and permissions.                  |
| **Amazon EC2**  | Verify read-only access control.                        |
| **Amazon RDS**  | Part of read-only policy for future database access.    |

---





