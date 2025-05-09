📘 README.md
markdown
Copy
Edit
# Terraform SNS → SQS → Lambda Integration

This project demonstrates how to use Terraform to provision AWS resources for an event-driven architecture using **SNS**, **SQS**, and **Lambda**, and how to test the flow using **boto3 (Python)**.

---

## 🚀 What It Does

- Creates an **SNS topic** to publish messages
- Creates an **SQS queue** subscribed to the SNS topic
- Creates a **Lambda function** triggered by messages in the SQS queue
- Sends a test message using Python (`boto3`)
- Verifies the message appears in SQS and gets printed in **CloudWatch Logs** by the Lambda function

---

## 📁 Files Included

- `main.tf` – Terraform script to deploy SNS, SQS, IAM roles, Lambda, and event mapping
- `lambda_function.py` – Lambda function code to process SQS messages
- `sns_sqs_demo.py` – Python script to publish a message to SNS and verify it in SQS

---

## 🧪 How to Use

### 1. **Deploy Infrastructure**
```bash
terraform init
terraform apply
This will create all required AWS resources in us-east-1.

2. Package the Lambda Function
bash
Copy
Edit
zip lambda.zip lambda_function.py
Make sure lambda.zip is in the same directory as main.tf before applying Terraform.

3. Run the Python Script
Update sns_sqs_demo.py with your actual SNS topic ARN and SQS queue URL (printed after terraform apply) and run:

bash
Copy
Edit
python sns_sqs_demo.py
4. Check Logs
Go to AWS Console → CloudWatch Logs → /aws/lambda/lambda_sqs_logger
You should see the printed message from SQS.

✅ Prerequisites
AWS account
Terraform installed
Python with boto3 installed
AWS credentials configured (via ~/.aws/credentials or environment variables)

📝 Notes
The lambda_function.py is triggered automatically when a message arrives in SQS.
The script sns_sqs_demo.py verifies message flow from SNS → SQS.
IAM permissions are configured for secure SNS-to-SQS access and Lambda logging.

