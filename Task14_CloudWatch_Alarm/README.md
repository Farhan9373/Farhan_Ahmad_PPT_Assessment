## Objective
Create a CloudWatch alarm to monitor EC2 CPU usage and automatically stop the instance and send an email when CPU exceeds 70%.

## Steps
Create SNS topic

Go to SNS → Topics → Create topic
Type: Standard
Provide topic name
Create email subscription

Protocol: Email
Enter email address
Confirm subscription from email inbox
Open CloudWatch

Go to CloudWatch → Alarms → Create alarm
Select metric

Choose EC2 → Per-Instance Metrics
Select CPUUtilization for the EC2 instance
Configure condition

Threshold type: Static
Whenever CPUUtilization ≥ 70%
Period: 1 minutes
Configure actions

Notification: Select SNS topic
EC2 Action: Stop this instance
Create alarm

Generate load on EC2 (optional) sudo apt update -y sudo apt install stress -y stress --cpu 2 --timeout 300

Wait for alarm to trigger

## Result
An email notification is received and the EC2 instance automatically stops when CPU utilization exceeds 70%.