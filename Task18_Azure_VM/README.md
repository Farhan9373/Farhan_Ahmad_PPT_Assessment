## Objective
Launch and configure a basic virtual machine in Azure and access it remotely.

## Steps
Open Azure Portal

Go to Virtual Machines → Create → Azure Virtual Machine
Configure basics

Resource group: create new
Virtual machine name: myvm
Region: any region
Image: Ubuntu Server
Size: Standard B1s
Authentication

Username: azureuser
Authentication type: Password
Set password
Inbound port rules

Allow SSH (Port 22)
Review and create

Click Create and wait for deployment
Get public IP address

Open the VM → Overview → Copy Public IP
Connect to VM ssh azureuser@

Verify connection whoami

## Result
The Azure virtual machine is successfully deployed and accessible through SSH.