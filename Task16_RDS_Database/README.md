# Task 16: RDS Database + SQL Workbench Connection & Queries

## Simple Definition
Created and connected to a managed relational database using Amazon RDS and executed basic SQL queries using MySQL Workbench.

---

## Objective
Understand managed database services in AWS and perform basic SQL operations.

---

## Services Used

- Amazon RDS (MySQL)
- VPC (Default)
- Security Group
- MySQL Workbench

---

## Step 1: RDS Database Creation

- Engine: MySQL
- Template: Free Tier
- DB Instance Identifier: task16-db
- Master Username: admin
- Port: 3306
- Public Access: Enabled
- VPC: Default VPC

Status verified as: **Available**

---

## Step 2: Security Group Configuration

Inbound Rule Added:

- Type: MySQL/Aurora
- Port: 3306
- Source: My IP

This allowed MySQL Workbench to connect securely to the RDS instance.

---

## Step 3: MySQL Workbench Connection Details

- Connection Name: Task16-RDS
- Connection Method: Standard (TCP/IP)
- Hostname: RDS Endpoint
- Port: 3306
- Username: admin
- Password: (Stored in Vault)

Connection tested successfully.

---

## Step 4: SQL Queries Executed

### Create Database

CREATE DATABASE task16db;

### Use Database

USE task16db;

### Create Table

CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    department VARCHAR(50),
    marks INT
);

### Insert Data

INSERT INTO students VALUES
(1, 'Farhan', 'CSE', 85),
(2, 'Aman', 'IT', 78),
(3, 'Neha', 'ECE', 92);

### View Data

SELECT * FROM students;

## Output

The SELECT query successfully displayed inserted student records in MySQL Workbench.

---

## Key Concepts Learned

- Amazon RDS is a managed relational database service.
- Public access must be enabled for external connections.
- Security Groups control database connectivity.
- Port 3306 is used for MySQL.
- SQL queries can be executed remotely using MySQL Workbench.
