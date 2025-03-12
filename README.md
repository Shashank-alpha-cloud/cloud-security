# cloud-security
# IMPLEMENT-IAM-POLICIES-SECURE-STORAGE-AND-DATA-ENCRYPTION-ON-A-CLOUD-PLATFORM.

COMPANY: CODTECH IT SOLUTIONS

NAME: Shashank

INTERN ID: :CT6WUSP

DOMAIN: Cloud Computing

DURATION: 6 WEEEKS

MENTOR: NEELA SANTOSH

Task 4

Implementing IAM (Identity and Access Management) policies, secure storage, and data encryption on a cloud platform involves several steps. Below is a detailed guide to achieve this on a popular cloud platform like **AWS (Amazon Web Services)**. The steps can be adapted to other cloud platforms like Azure or Google Cloud with similar concepts.

---

### **Step 1: Define the Scope and Requirements**
1. **Identify the Data and Resources**: Determine which data and resources need to be secured (e.g., S3 buckets, EC2 instances, RDS databases).
2. **Define Access Levels**: Identify who needs access to what resources (e.g., developers, admins, auditors).
3. **Compliance Requirements**: Ensure the setup meets compliance standards like GDPR, HIPAA, or PCI-DSS if applicable.

---

### **Step 2: Set Up IAM Policies**
IAM policies control who can access what resources and what actions they can perform.

#### **2.1 Create IAM Users and Groups**
1. **Log in to AWS Management Console** and navigate to the **IAM** service.
2. **Create IAM Users**:
   - Go to **Users** > **Add User**.
   - Enter the username and select the access type (Programmatic access, AWS Management Console access, or both).
   - Set permissions by adding the user to a group or attaching policies directly.
3. **Create IAM Groups**:
   - Go to **Groups** > **Create New Group**.
   - Name the group (e.g., `Developers`, `Admins`).
   - Attach policies to the group (e.g., `AmazonS3FullAccess`, `AmazonEC2ReadOnlyAccess`).
4. **Add Users to Groups**: Assign users to the appropriate groups based on their roles.

#### **2.2 Create Custom IAM Policies**
1. Go to **Policies** > **Create Policy**.
2. Use the **Visual Editor** or **JSON** to define the policy.
   - Example JSON policy for allowing read-only access to an S3 bucket:
     ```json
     {
       "Version": "2012-10-17",
       "Statement": [
         {
           "Effect": "Allow",
           "Action": [
             "s3:GetObject",
             "s3:ListBucket"
           ],
           "Resource": [
             "arn:aws:s3:::example-bucket",
             "arn:aws:s3:::example-bucket/*"
           ]
         }
       ]
     }
     ```
3. Attach the custom policy to users or groups.

#### **2.3 Enable Multi-Factor Authentication (MFA)**
1. Go to **Users** > Select a user > **Security Credentials**.
2. Enable MFA and follow the prompts to set it up.

#### **2.4 Set Up IAM Roles for Services**
1. Go to **Roles** > **Create Role**.
2. Select the service that will use the role (e.g., EC2, Lambda).
3. Attach policies to the role (e.g., `AmazonS3ReadOnlyAccess`).
4. Assign the role to the service.

---

### **Step 3: Secure Storage**
Secure storage involves configuring storage services like S3 to ensure data is protected.

#### **3.1 Enable S3 Bucket Encryption**
1. Go to the **S3** service and select a bucket.
2. Go to **Properties** > **Default Encryption**.
3. Enable encryption using **SSE-S3** (AWS-managed keys) or **SSE-KMS** (customer-managed keys).

#### **3.2 Configure S3 Bucket Policies**
1. Go to the bucket’s **Permissions** tab.
2. Add a bucket policy to restrict access:
   - Example policy to allow access only from specific IPs:
     ```json
     {
       "Version": "2012-10-17",
       "Statement": [
         {
           "Effect": "Deny",
           "Principal": "*",
           "Action": "s3:*",
           "Resource": [
             "arn:aws:s3:::example-bucket",
             "arn:aws:s3:::example-bucket/*"
           ],
           "Condition": {
             "NotIpAddress": {
               "aws:SourceIp": ["192.0.2.0/24"]
             }
           }
         }
       ]
     }
     ```

#### **3.3 Enable Versioning and Logging**
1. Go to the bucket’s **Properties** tab.
2. Enable **Versioning** to keep multiple versions of objects.
3. Enable **Server Access Logging** to track access requests.

---

### **Step 4: Implement Data Encryption**
Encrypt data at rest and in transit.

#### **4.1 Encrypt Data at Rest**
1. **S3**: Enable default encryption as described in Step 3.1.
2. **RDS**: Enable encryption when creating the database instance.
   - Go to **RDS** > **Create Database**.
   - Enable encryption and select a KMS key.
3. **EBS Volumes**: Enable encryption when creating EC2 instances or EBS volumes.
   - Go to **EC2** > **Volumes** > Create Volume.
   - Enable encryption and select a KMS key.

#### **4.2 Encrypt Data in Transit**
1. Use **HTTPS** for web traffic.
2. Use **SSL/TLS** for database connections.
   - For RDS, enable SSL/TLS and configure the client to use it.
3. Use **AWS Certificate Manager (ACM)** to manage SSL/TLS certificates for load balancers and CloudFront distributions.

---

### **Step 5: Monitor and Audit**
1. **Enable CloudTrail**:
   - Go to **CloudTrail** > **Create Trail**.
   - Enable logging for all regions and store logs in an S3 bucket.
2. **Enable AWS Config**:
   - Go to **AWS Config** > **Get Started**.
   - Enable recording and specify an S3 bucket for logs.
3. **Set Up CloudWatch Alarms**:
   - Go to **CloudWatch** > **Alarms** > Create Alarm.
   - Monitor metrics like unauthorized access attempts or encryption failures.

---

### **Step 6: Generate the Report**
1. Document all configurations:
   - IAM users, groups, roles, and policies.
   - S3 bucket policies, encryption settings, and logging.
   - Encryption settings for RDS, EBS, and other services.
   - CloudTrail and AWS Config settings.
2. Include screenshots and code snippets for clarity.
3. Provide recommendations for ongoing monitoring and improvements.

---

### **Step 7: Test and Validate**
1. Test IAM policies by logging in as different users and verifying access.
2. Verify encryption settings for S3, RDS, and EBS.
3. Check CloudTrail logs and AWS Config rules for compliance.

---

By following these steps, you will have a secure cloud environment with IAM policies, secure storage, and data encryption configured. The final report should detail all configurations and provide evidence of compliance with security best practices.


#I have also attached screenshots

![Image](https://github.com/user-attachments/assets/57011722-aa58-40fe-b624-51fb18f01647)

![Image](https://github.com/user-attachments/assets/5a86a4b0-3b4e-4189-a813-5ae027db0b1c)




This internship has been an invaluable learning experience, providing me with the opportunity to apply theoretical knowledge to real-world scenarios and gain hands-on experience in cloud computing,Working on projects such has significantly enhanced my technical skills and deepened my understanding of  AWS,security best practices,
I am deeply grateful to CodTech  for giving me this opportunity to grow both professionally and personally. A special thanks to my mentor NEELA SANTOSH  and the entire team for their guidance, support, and encouragement throughout this journey. Their expertise and willingness to share knowledge have been instrumental in shaping my learning experience.
This internship has not only strengthened my technical abilities but also improved my problem-solving, teamwork, and communication skills. I am confident that the skills and knowledge I have gained will serve as a strong foundation for my future career.
Once again, I would like to express my heartfelt gratitude to everyone at CodTech  for making this internship a memorable and enriching experience. I look forward to applying what I have learned and contributing to the field in the future.




