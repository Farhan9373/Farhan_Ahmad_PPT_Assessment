## Objective
Monitor a website and send an alert email if the website becomes unavailable.

## Steps
Create SNS topic

Go to SNS → Topics → Create topic
Type: Standard
Provide topic name
Create email subscription

Protocol: Email
Enter email address
Confirm the subscription from email inbox
Open CloudWatch

Go to CloudWatch → Synthetics Canaries → Create canary
Configure Canary

Blueprint: Heartbeat monitoring
Provide website URL
Schedule: Every 5 minutes
Runtime: Python
Configure IAM role

Allow CloudWatch Synthetics permissions
Create alarm

Go to CloudWatch → Alarms → Create alarm
Metric: Canary Failed
Threshold: greater than 0
Add notification

Select SNS topic created earlier
Test monitoring

Stop the website or provide invalid URL
Wait for monitoring interval
Check email notification

## Result
An alert email is received when the monitored website becomes unavailable.