# AWS IAM (Identity and Access Management) Guide

## 📌 Introduction

AWS IAM (Identity and Access Management) is a security service that helps you **control who can access AWS resources and what they can do**.

Think of IAM like a security system:

- **Who can enter?** (Users, Groups, Roles)
- **What can they do?** (Permissions, Policies)

IAM allows you to **secure AWS accounts** by managing authentication and authorization.

---

## 📚 Key IAM Concepts

### 1️⃣ IAM Users 👤

- An **IAM User** represents a person or application with AWS access.
- Users can have:
  - A **username and password** for AWS Management Console login.
  - **Access keys** for API or CLI access.
- Each user should have only the **necessary permissions** for security.

### 2️⃣ IAM Groups 👥

- A **group** is a collection of IAM users.
- Instead of assigning permissions individually, users inherit permissions from the group.
- Example IAM Groups:
  - **Developers** → Access to EC2 and S3.
  - **Admins** → Full AWS access.
  - **Billing** → Access to billing services only.

### 3️⃣ IAM Roles 🎭

- **Roles** allow AWS services or users to assume temporary permissions.
- Unlike users, roles **don’t have passwords or access keys**.
- Example use cases:
  - **EC2 accessing S3** → Attach an IAM role to EC2.
  - **Lambda writing to DynamoDB** → Assign a role to Lambda.
  - **Cross-Account Access** → A role lets users from one AWS account access another.

### 4️⃣ IAM Policies 📜

- **Policies define what actions users, groups, or roles can perform**.
- Policies are written in **JSON format** and consist of:
  - **Effect** → Allow or Deny access.
  - **Action** → What AWS services/actions are allowed.
  - **Resource** → Which AWS resource can be accessed.
- Example policy allowing read-only access to an S3 bucket:
  ```json
  {
    "Version": "2012-10-17",
    "Statement": [
      {
        "Effect": "Allow",
        "Action": "s3:ListBucket",
        "Resource": "arn:aws:s3:::my-bucket"
      }
    ]
  }
  ```

### 5️⃣ IAM Authentication Methods 🔑

IAM supports multiple authentication methods:

1. **Username & Password** → For AWS Console login.
2. **Access Keys (API/CLI Access)** → Generated keys for API requests.
3. **MFA (Multi-Factor Authentication)** → Adds an extra security layer.
4. **Federated Access** → Use external identity providers (Google, Okta, etc.).

---

## 🛡️ IAM Best Practices ✅

1. **Least Privilege Principle** → Grant only necessary permissions.
2. **Use IAM Roles** → Instead of embedding credentials in applications.
3. **Enable Multi-Factor Authentication (MFA)** for all users.
4. **Rotate Access Keys Regularly** and avoid long-term access keys.
5. **Use IAM Groups** → Assign permissions at the group level, not per user.
6. **Monitor IAM Activity** using AWS CloudTrail.
7. **Apply IAM Conditions** → Restrict access based on IP, time, or device.

---

## 🔥 Intermediate IAM Concepts

### 🔹 Service Control Policies (SCPs)

- Used in **AWS Organizations** to apply permissions across multiple AWS accounts.
- SCPs act as a **security guardrail** for all users, roles, and accounts.

### 🔹 IAM Conditions

- Apply additional rules like:
  - Restricting access based on **IP Address**.
  - Allowing access only **during business hours**.
- Example policy allowing S3 access **only from a specific IP range**:
  ```json
  {
    "Version": "2012-10-17",
    "Statement": [
      {
        "Effect": "Allow",
        "Action": "s3:*",
        "Resource": "arn:aws:s3:::my-bucket",
        "Condition": {
          "IpAddress": {
            "aws:SourceIp": "192.168.1.0/24"
          }
        }
      }
    ]
  }
  ```

---

## 🔹 Cross-Account Access

Allows users from one AWS account to access resources in another AWS account via **IAM roles**.

---

## 🔹 Identity Providers (IdP)

IAM can integrate with **external identity providers** like:

- Google
- Okta
- Microsoft Active Directory

Enables **Single Sign-On (SSO)** for seamless authentication.

---

## 🚀 Advanced IAM Concepts

### 🔥 AWS IAM Identity Center (SSO)

- **AWS IAM Identity Center (formerly AWS SSO)** allows **centralized user management**.
- Users can log in once and access **multiple AWS accounts**.

### 🔥 Attribute-Based Access Control (ABAC)

- Instead of static permissions, **ABAC assigns permissions based on tags (attributes)**.
- **Example:** Allow access only to employees with the tag → `Department=Finance`.

### 🔥 AWS IAM Access Analyzer

- **Detects overly permissive policies** and helps improve security.

### 🔥 Custom IAM Policies with Advanced Conditions

- **Example:** Allow access to AWS only during business hours **(9 AM - 5 PM UTC)**.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "*",
      "Resource": "*",
      "Condition": {
        "DateGreaterThan": { "aws:CurrentTime": "09:00:00" },
        "DateLessThan": { "aws:CurrentTime": "17:00:00" }
      }
    }
  ]
}
```

---

## 🔎 IAM Monitoring & Auditing

### ✅ AWS CloudTrail

- Logs all **IAM activity** (who accessed what, when, and from where).

### ✅ AWS Config

- **Tracks changes** in IAM policies and roles over time.

### ✅ IAM Access Advisor

- Shows **when a user last accessed** a service.
- Helps **remove unused permissions** for better security.

---

## 🎯 Conclusion

AWS IAM is **essential for securing AWS accounts**. By following **best practices**, using **roles instead of users**, enabling **MFA**, and **monitoring IAM logs**, you can **protect AWS resources effectively**.
