# ☁️ AWS CloudTrail — Hands-on Practical

## 📌 Project Overview

This project covers hands-on learning and practical implementation of **AWS CloudTrail** for auditing, monitoring, and investigating AWS account activity.

## 🎯 What I Learned

- What is AWS CloudTrail
- Purpose of CloudTrail
- CloudTrail vs CloudWatch
- CloudTrail Events
- Management Events
- Data Events
- Event History
- Event details and filtering
- CloudTrail Trails
- Multi-Region Trail
- S3 log storage
- CloudTrail Log File Validation
- CloudWatch Logs integration
- Insights Events
- Network Activity Events
- Advanced Event Selectors
- CloudTrail security and auditing use cases

## 🛠️ Practical Implementation

### CloudTrail Trail Created

**Trail Name:** `pavan-cloudtrail`

The trail was configured as a **Multi-Region Trail** with management event logging and S3 log delivery.

### S3 Log Destination

CloudTrail logs are delivered to an S3 bucket:

`aws-cloudtrail-logs-224718142629-33549700`

CloudTrail log files were successfully delivered to the S3 bucket in compressed `.json.gz` format.

## 📊 Management Events

Management Events were configured to capture AWS management and administrative activities such as:

- EC2 instance creation/deletion
- IAM user changes
- Security Group changes
- AWS resource configuration changes

## 📦 Data Events

S3 Data Events were configured using **Advanced Event Selectors**.

### Configuration

```json
[
  {
    "FieldSelectors": [
      {
        "Field": "eventCategory",
        "Equals": [
          "Data"
        ]
      },
      {
        "Field": "resources.type",
        "Equals": [
          "AWS::S3::Object"
        ]
      },
      {
        "Field": "resources.ARN",
        "StartsWith": [
          "arn:aws:s3:::pavan-s3-storage-01-224718142629-ap-south-1-an/"
        ]
      },
      {
        "Field": "readOnly",
        "Equals": [
          "true"
        ]
      }
    ]
  }
]
