## Task 9 – Access S3 from EC2 using IAM Role

## Objective
To allow an EC2 instance to access Amazon S3 securely using an IAM Role, without using access keys.

## Services Used
Amazon EC2
AWS IAM (Role & Policy)
Amazon S3
AWS CLI v2

## Steps Performed
Created an S3 bucket for testing access.
Created an IAM role for EC2 and attached the AmazonS3FullAccess policy.
Attached the IAM role to an EC2 instance.
Connected to the EC2 instance.
Installed AWS CLI v2 manually on the EC2 instance.
Verified that the EC2 instance assumed the IAM role.
Verified access to Amazon S3 from the EC2 instance using AWS CLI commands.
Confirmed that no access keys were configured.
