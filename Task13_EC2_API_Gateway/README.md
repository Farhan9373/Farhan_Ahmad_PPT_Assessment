# Task 13: Start/Stop EC2 using Lambda + API Gateway

## Simple Definition
Automated EC2 start and stop operations using AWS Lambda triggered by API Gateway.

## Objective
Understand serverless automation using API Gateway and Lambda.

---

## Architecture

API Gateway → Lambda Function → EC2 Instance

---

## Services Used

- AWS Lambda
- API Gateway
- EC2
- IAM Role

---

## Implementation Steps

### 1. Created IAM Role
Role Name: LambdaEC2ControlRole  
Policy Attached: AmazonEC2FullAccess  

### 2. Created Lambda Function
Function Name: EC2ControlFunction  
Runtime: Python 3.12  
Execution Role: LambdaEC2ControlRole  

Lambda Code:

```python
import json
import boto3

ec2 = boto3.client('ec2')

def lambda_handler(event, context):
    
    instance_id = "YOUR_INSTANCE_ID"
    action = event.get('action', 'start')

    if action == 'start':
        ec2.start_instances(InstanceIds=[instance_id])
        return {
            'statusCode': 200,
            'body': json.dumps('EC2 Instance Started')
        }
    
    elif action == 'stop':
        ec2.stop_instances(InstanceIds=[instance_id])
        return {
            'statusCode': 200,
            'body': json.dumps('EC2 Instance Stopped')
        }
    
    else:
        return {
            'statusCode': 400,
            'body': json.dumps('Invalid Action')
        }

        
## Test Lambda

Create test event { "action": "start" }
Create API Gateway

Go to API Gateway → Create API → HTTP API
Create route: /ec2
Method: POST
Integration: Lambda function
Deploy API

Create stage and deploy
Copy Invoke URL
Test using browser or Postman

POST request body: { "action": "stop" }
Verify EC2 instance state in EC2 console

## Result
The EC2 instance starts or stops successfully using the API endpoint.