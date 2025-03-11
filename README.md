# AWS Cost Optimization Using Lambda

## Description
This project automates the cleanup of stale EBS snapshots using **AWS Lambda** and **Python (Boto3)**. It helps reduce storage costs by identifying and deleting snapshots linked to deleted or unattached volumes.

---

## How It Works
1. The Lambda function lists all EBS snapshots in the AWS account.  
2. It retrieves all active EC2 instances (running and stopped).  
3. If a snapshot is linked to a volume that is no longer attached to an instance, the function deletes the snapshot.  

---

## Setup
### 1. Create a Lambda Function  
- Create a new Lambda function with the **Python 3.10** runtime.  
- Upload the `ebs_stale_snapshots.py` file.  

### 2. Set Permissions  
- Go to **Configuration → Permissions** and select the Lambda role.  
- Attach the following inline policy:  
   - `ec2:DescribeSnapshots`  
   - `ec2:DeleteSnapshot`  
   - `ec2:DescribeVolumes`  
   - `ec2:DescribeInstances`  

### 3. Testing  
- Create a test event in the Lambda function.  
- Run the function manually.  
- Confirm that stale snapshots are deleted from the AWS console.  

---

## Outcome
✅ Reduced storage costs by deleting unused EBS snapshots.  
✅ Automated cleanup to avoid manual effort.  

---

## Technologies Used
- AWS Lambda  
- Python  
- Boto3  
- EC2  
- EBS  
- IAM  

---

## Why It Matters
EBS snapshots are charged based on storage usage. Retaining unused snapshots increases AWS costs unnecessarily. Automating cleanup ensures that you're only paying for the storage you need.  

---

## How to Test
1. Manually create an EC2 instance and take a snapshot of its volume.  
2. Delete the instance but keep the snapshot.  
3. Trigger the Lambda function manually.  
4. Confirm that the stale snapshot is deleted.  

---

## Next Steps
- Automate Lambda invocation using **CloudWatch** to run the cleanup periodically.  
- Set up notifications using **SNS** to monitor deletion activity.  

---

### ✅ Status: **Completed**  
⭐ Feel free to customize or improve as needed!  

---

### 💡 **Pro Tip:**  
Add logs using `print()` or `logging` to track the function's activity and simplify debugging.  

---

### 🔗 **GitHub:** [https://github.com/Benny-17](https://github.com/Benny-17)  
