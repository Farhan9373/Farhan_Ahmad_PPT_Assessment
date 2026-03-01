## Task 4: ASG and ELB in EC2
## Aim

To configure an Auto Scaling Group (ASG) with a Load Balancer in EC2.

## Objective

To understand high availability and automatic scaling of EC2 instances based on demand.

##  Explanation

Auto Scaling Group (ASG) automatically launches or terminates EC2 instances based on defined conditions.

Elastic Load Balancer (ELB) distributes incoming traffic across multiple EC2 instances to ensure high availability and fault tolerance.

By combining ASG and ELB:

Traffic is balanced across instances

If one instance fails, traffic goes to healthy instances

New instances are automatically launched when needed

## Steps Performed
Step 1: Create Launch Template

Go to AWS Console

Open EC2 Dashboard

Click Launch Templates

Click Create Launch Template

Provide template name

Select Ubuntu AMI

Choose instance type (t2.micro)

Select key pair

Configure Security Group (Allow HTTP – Port 80)

Add user data (optional for installing Nginx automatically)

Click Create Launch Template

## Step 2: Create Load Balancer (ELB)

Go to EC2 Dashboard

Click Load Balancers

Click Create Load Balancer

Choose Application Load Balancer

Provide name

Choose Internet-facing

Select VPC

Select at least two subnets (different AZs)

Create Target Group

Click Create Load Balancer

## Step 3: Create Target Group

Choose Instances as target type

Select HTTP (Port 80)

Select VPC

Create target group

(Instances will be automatically registered when ASG is attached.)

## Step 4: Create Auto Scaling Group

Go to Auto Scaling Groups

Click Create Auto Scaling Group

Select Launch Template

Choose VPC and Subnets (minimum two AZs)

Attach to existing Load Balancer

Select the created Target Group

Set Desired Capacity (example: 2)

Set Minimum and Maximum capacity (example: Min 1, Max 3)

Configure scaling policy (optional: Target tracking policy based on CPU)

Click Create Auto Scaling Group

## Step 5: Verification

Check EC2 Instances (should launch automatically)

Open Load Balancer DNS name in browser

Website should load

Stop one instance and verify new instance is launched automatically