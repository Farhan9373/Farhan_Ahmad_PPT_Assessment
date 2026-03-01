# Task 6: S3 Replication and Lifecycle Policy

## Aim

To configure replication and lifecycle rules in Amazon S3.

## Objective

To understand how S3 replication works for backup purposes and how lifecycle policies help in cost optimization.

---

## Explanation

S3 Replication is used to automatically copy objects from one bucket to another bucket (usually in a different region).

Lifecycle Policy is used to automatically move objects to cheaper storage classes or delete them after a certain time to reduce storage cost.

Before enabling replication, versioning must be enabled on both source and destination buckets.

---

## Steps Performed

### Step 1: Create Two S3 Buckets

1. Go to AWS Console
2. Open S3 service
3. Click Create Bucket
4. Create Source Bucket
5. Create Destination Bucket (can be in same or different region)

---

### Step 2: Enable Versioning

1. Open Source Bucket

2. Go to Properties

3. Enable Versioning

4. Open Destination Bucket

5. Go to Properties

6. Enable Versioning

Versioning must be enabled for replication to work.

---

### Step 3: Configure Replication

1. Open Source Bucket
2. Go to Management tab
3. Click Create Replication Rule
4. Choose to replicate all objects
5. Select Destination Bucket
6. Create or select IAM Role
7. Save the rule

Now, when a new file is uploaded to source bucket, it will automatically replicate to destination bucket.

---

### Step 4: Configure Lifecycle Policy

1. Open Source Bucket
2. Go to Management tab
3. Click Create Lifecycle Rule
4. Give rule name
5. Apply to all objects
6. Choose transition action
   Example:

   * Move to Standard-IA after 30 days
   * Move to Glacier after 60 days
7. (Optional) Set expiration after certain days
8. Save rule

This helps reduce storage cost automatically.
