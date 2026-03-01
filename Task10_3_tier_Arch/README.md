# Task 10: VPC 3-Tier Architecture

## Simple Definition
Designed a 3-tier architecture using AWS VPC with public and private subnets.

## Objective
Understand networking, NAT, IGW, NACL, and SSH tunneling.

---

## Architecture

Internet → IGW → Public Subnet (Web/Bastion)
Private App Subnet → NAT Gateway → Internet
Private DB Subnet → No direct Internet

---

## Components Used

- VPC (10.0.0.0/16)
- 3 Subnets (Public, Private-App, Private-DB)
- Internet Gateway
- NAT Gateway
- Route Tables
- Security Groups
- EC2 Instances

---

## Implementation Steps

1. Created VPC with CIDR 10.0.0.0/16
2. Created 3 subnets:
   - Public: 10.0.1.0/24
   - Private-App: 10.0.2.0/24
   - Private-DB: 10.0.3.0/24
3. Attached Internet Gateway
4. Configured Public Route Table with IGW
5. Created NAT Gateway in Public Subnet
6. Updated Private-App route table with NAT
7. Launched EC2 instances in respective subnets
8. Configured Security Groups
9. Tested SSH tunneling via Bastion host

---

## Key Concepts Learned

- IGW allows public internet access
- NAT Gateway allows outbound internet for private subnet
- DB tier remains isolated
- Bastion host enables secure SSH access
- Security Groups = Stateful firewall
- NACL = Stateless firewall