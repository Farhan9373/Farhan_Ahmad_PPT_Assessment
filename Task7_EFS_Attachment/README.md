# Task 7 – Create EFS and Connect to Multiple Instances

## Objective

Mount shared storage across multiple EC2 instances using Amazon EFS.

This task demonstrates how to connect two instances (Ubuntu and Amazon Linux) to the same shared file system using:

* Amazon EC2
* Amazon Elastic File System
* NFS protocol (Port 2049)

---

# Architecture

* 1 Ubuntu EC2 Instance
* 1 Amazon Linux EC2 Instance
* 1 EFS File System
* Both instances in same VPC
* Security Group allowing NFS (2049)

---

# Step 1: Launch EC2 Instances

Launch two instances:

1. Ubuntu 22.04
2. Amazon Linux

Ensure:

* Both are in the same VPC
* Same Security Group
* Security Group allows:

  * SSH (22) from your IP
  * NFS (2049) from EC2 Security Group

---

# Step 2: Create EFS

1. Go to AWS Console → EFS
2. Click Create File System
3. Select same VPC as EC2
4. Create
5. Wait until status = Available
6. Copy DNS name

Example:

```
fs-0089178069181b9e5.efs.eu-north-1.amazonaws.com
```

---

# Step 3: Mount EFS on Ubuntu Instance

SSH into Ubuntu:

Update packages:

```bash
sudo apt update
```

Install NFS client:

```bash
sudo apt install nfs-common -y
```

Create mount directory:

```bash
sudo mkdir -p /mnt/efs
```

Mount EFS:

```bash
sudo mount -t nfs4 fs-0089178069181b9e5.efs.eu-north-1.amazonaws.com:/ /mnt/efs
```

Verify:

```bash
df -h
```

---

# Step 4: Mount EFS on Amazon Linux Instance

SSH into Amazon Linux:

Install NFS utilities:

```bash
sudo yum install nfs-utils -y
```

Create mount directory:

```bash
sudo mkdir -p /mnt/efs
```

Mount EFS:

```bash
sudo mount -t nfs4 fs-0089178069181b9e5.efs.eu-north-1.amazonaws.com:/ /mnt/efs
```

Verify:

```bash
df -h
```

---

# Step 5: Test Shared Storage

On Ubuntu instance:

```bash
cd /mnt/efs
echo "Hello from Ubuntu" | sudo tee test.txt
```

Now go to Amazon Linux instance:

```bash
cd /mnt/efs
cat test.txt
```

If you see:

```
Hello from Ubuntu
```

✅ Shared storage is working successfully.

---

# Step 6: Make Mount Persistent (Optional)

Edit fstab:

```bash
sudo nano /etc/fstab
```

Add:

```
fs-0089178069181b9e5.efs.eu-north-1.amazonaws.com:/ /mnt/efs nfs4 defaults,_netdev 0 0
```

Save and test:

```bash
sudo mount -a
```

---

# Verification Commands

Check mount:

```bash
df -h
```

Check specifically:

```bash
mount | grep efs
```

Check directory:

```bash
ls /mnt/efs
```

---

# Troubleshooting

If mount freezes:

* Check EFS Security Group
* Allow NFS (2049)
* Source must be EC2 Security Group
* Ensure both are in same VPC

Cancel frozen mount:

```
Ctrl + C
```

---

# Screenshots Required

1. EFS File System (Available state)
2. df -h showing EFS mounted
3. Shared file visible on second instance

---

# Conclusion

Successfully mounted a single EFS file system across two different Linux instances (Ubuntu and Amazon Linux) and verified shared file access.
