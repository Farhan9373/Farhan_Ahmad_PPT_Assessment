Task 3: Attach EBS Volume from Different AZ using Snapshot

 Aim

To create a snapshot of an EBS volume and use it to create a new volume in another Availability Zone, then attach it to an EC2 instance.

Objective

To understand how EBS snapshots work and how storage can be moved across Availability Zones.

---

 Explanation

An EBS volume can only be attached to an EC2 instance in the same Availability Zone.
If we want to use the same data in another AZ, we cannot directly attach the volume.

So the process is:

1.Create snapshot of the existing volume
2.Create new volume from that snapshot in another AZ
3.Attach the new volume to EC2

---

Steps Performed

Step 1: Create Snapshot

1.Go to AWS Console
2.Open EC2 Dashboard
3.Click on Volumes
4.Select the existing EBS volume
5.Click Actions
6.Click Create Snapshot
7.Give description and create snapshot
8.Wait until snapshot status shows Completed

---

Step 2: Create Volume in Different AZ

1.Go to Snapshots
2.Select the snapshot created
3.Click Actions
4.Click Create Volume
5.Choose a different Availability Zone
6.Click Create Volume

Now new volume is created in another AZ.

---

 Step 3: Attach Volume to EC2

1.Go to Volumes
2.Select the new volume
3.Click Actions
4.Click Attach Volume
5.Select EC2 instance in same AZ
6.Give device name (example: /dev/sdf)
7.Click Attach
