# AWS Event Driven Architecture

##  Overview
This project demonstrates a **serverless event-driven architecture** using **AWS S3, SNS, SQS, and Lambda**.  
When a file is uploaded to an S3 bucket, an SNS topic sends notifications to SQS queues and an email subscriber.  
The SQS queues trigger Lambda functions to process the uploaded file automatically.


---

##  Architecture Diagram

![Screenshot_24-10-2025_41226_lucid app](https://github.com/user-attachments/assets/e7c1c132-c770-4a49-aa72-1aa9db49bea7)


---

##  Architecture Flow

1. **S3 Bucket (Trigger Source)**  
   - When a file is uploaded, S3 triggers an event notification.

2. **SNS Topic (Event Distributor)**  
   - Receives notifications from S3 and distributes them to multiple targets:
     - **SQS Queues** — for processing
     - **Email Subscribers** — for alerting

3. **SQS Queues (Message Buffer)**  
   - Reliable message queue between SNS and Lambda.
   - Holds messages until Lambda successfully processes them.

4. **Lambda Functions (Processing Layer)**  
   - Consumes messages from SQS.
   - Executes custom logic (e.g., log details, process data, or trigger downstream tasks).

5. **Email Notifications (Alert System)**  
   - Sends email notifications whenever a file is uploaded to S3.

---

##  AWS Resources Used

| Service | Example Name | Purpose |
|----------|---------------|----------|
| **S3** | `mybucket` | Stores uploaded files |
| **SNS** | `mytopic` | Publishes S3 notifications |
| **SQS** | `queue1`, `queue2` | Queues SNS messages |
| **Lambda** | `mylambda1`, `mylambda2` | Processes queued messages |
| **IAM** | Custom Roles/Policies | Secure service access |



