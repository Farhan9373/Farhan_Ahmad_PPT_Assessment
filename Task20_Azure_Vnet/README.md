# Task 20: Azure VNet (Basic Networking Practical)

## Simple Definition
Configured Azure Virtual Network, subnet, and Network Security Group rules.

## Objective
Understand basic cloud networking in Azure.

---

## Services Used

- Azure Virtual Network (VNet)
- Subnet
- Network Security Group (NSG)

---

## Implementation Steps

### 1. Created Virtual Network
- Name: VNet-Task20
- Address Space: 10.0.0.0/16
- Resource Group: RG-Task20

### 2. Created Subnet
- Name: Subnet-1
- Address Range: 10.0.1.0/24

### 3. Created Network Security Group
- Name: NSG-Task20

### 4. Added Inbound Rule
- Protocol: TCP
- Port: 22 (SSH)
- Action: Allow
- Priority: 1000

### 5. Associated NSG with Subnet

---

## Concepts Learned

- VNet provides isolated network in Azure
- Subnet divides network for logical separation
- NSG controls inbound and outbound traffic
- Port 22 used for SSH access (Linux)

---