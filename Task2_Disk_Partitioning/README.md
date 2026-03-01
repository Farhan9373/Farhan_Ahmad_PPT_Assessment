
Task 2: Disk Partitioning (Ubuntu – MBR & Windows – GPT)

Project Title

Disk Partitioning using MBR (Ubuntu) and GPT (Windows)

Objective

To understand disk structure and learn how to create and manage disk partitions using MBR in Ubuntu (Linux) and GPT in Windows.


 Part 1: Disk Partitioning in Ubuntu using MBR (fdisk)

 Step 1: Check Available Disks

Open terminal and run:

lsblk

This shows available disks and partitions.

Step 2: Select the Disk

Use fdisk to manage the disk (example disk: /dev/sdb):

sudo fdisk /dev/sdb

Step 3: Create MBR Partition Table

Inside fdisk, press:

o

This creates a new DOS partition table (MBR).

---

Step 4: Create New Partition

Press:

n

Then choose:

1.p (Primary partition)
2.Partition number (1)
3.Press Enter for default first sector
4.Press Enter for default last sector (or specify size like +1G)

---

Step 5: Save Changes

Press:

w

This writes changes to disk and exits.

---

Step 6: Format the Partition

sudo mkfs.ext4 /dev/sdb1

---

Step 7: Verify Partition

lsblk

This confirms the partition is created.

---

Part 2: Disk Partitioning in Windows using GPT

Step 1: Open Disk Management

1.Press Windows + R
2.Type: diskmgmt.msc
3.Press Enter

---

Step 2: Initialize Disk as GPT

If the disk is new:

Right click on the disk
Select "Initialize Disk"
Choose GPT (GUID Partition Table)
Click OK

If converting:

Right click disk
-Convert to GPT Disk

---

Step 3: Create New Volume

1.Right click on unallocated space
2.Select "New Simple Volume"
3.Click Next
4.Specify size
5.Assign drive letter
6.Choose file system (NTFS)
7.Click Finish

---

Difference Between MBR and GPT

MBR (Master Boot Record):

1.Supports up to 2 TB disk size
2.Maximum 4 primary partitions
3.Older partition style

GPT (GUID Partition Table):

1.Supports disks larger than 2 TB
2.Allows many partitions
3.More reliable and modern

---

Commands Used in Ubuntu (Proof)

lsblk
sudo fdisk /dev/sdb
sudo mkfs.ext4 /dev/sdb1

