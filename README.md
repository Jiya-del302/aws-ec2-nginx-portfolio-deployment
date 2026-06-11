# AWS EC2 Nginx Portfolio Deployment

## Project Overview

This project demonstrates the deployment of a personal portfolio website on an AWS EC2 Ubuntu server using Nginx as a web server. The deployment follows cloud infrastructure best practices by creating a custom VPC, configuring networking components, securing the instance using Security Groups, and hosting a static portfolio website.

The project covers the complete deployment lifecycle, from infrastructure setup to making the website publicly accessible through the internet.

---

## Technologies Used

* Amazon Web Services (AWS)
* Amazon EC2
* Custom VPC
* Public Subnet
* Internet Gateway
* Route Tables
* Security Groups
* Ubuntu Server
* Nginx Web Server
* Git & Git Bash
* HTML5
* CSS3
* Linux Command Line

---

## Project Architecture

The deployment architecture consists of:

* Custom VPC
* Public Subnet
* Internet Gateway
* Route Table Configuration
* EC2 Ubuntu Instance
* Security Group Rules
* Nginx Web Server
* Portfolio Website

The website files are hosted on an Ubuntu EC2 instance and served through Nginx over HTTP.

---

## Deployment Workflow

### Step 1: Create a Custom VPC

A custom Virtual Private Cloud (VPC) was created to provide an isolated networking environment for the project.

**Purpose:**

* Network isolation
* Better control over resources
* Custom network configuration

---

### Step 2: Create a Public Subnet

A public subnet was created inside the VPC.

**Purpose:**

* Allows resources inside the subnet to communicate with the internet.

---

### Step 3: Configure Internet Gateway

An Internet Gateway (IGW) was attached to the VPC.

**Purpose:**

* Provides internet connectivity to resources inside the VPC.

---

### Step 4: Configure Route Table

A route table was created and associated with the public subnet.

**Route Added:**

Destination:

```
0.0.0.0/0
```

Target:

```
Internet Gateway
```

**Purpose:**

* Enables internet access for the EC2 instance.

---

### Step 5: Launch EC2 Ubuntu Instance

An EC2 instance was launched using Ubuntu Server.

**Configuration:**

* Ubuntu AMI
* Key Pair (.pem)
* Public IP Enabled
* Deployed inside the custom VPC and subnet

---

### Step 6: Configure Security Group

Inbound rules were added:

| Port | Protocol | Purpose        |
| ---- | -------- | -------------- |
| 22   | SSH      | Remote Access  |
| 80   | HTTP     | Website Access |

**Purpose:**

* SSH access from local machine
* Public website access through browser

---

### Step 7: Connect to EC2 Using Git Bash

SSH connection established using:

```bash
ssh -i my-key.pem ubuntu@<public-ip>
```

**Purpose:**

* Secure remote administration of the server

---

### Step 8: Install Nginx

Ubuntu packages were updated and Nginx was installed.

```bash
sudo apt update
sudo apt upgrade -y
sudo apt install nginx -y
```

Start Nginx:

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

Verify status:

```bash
sudo systemctl status nginx
```

---

### Step 9: Upload Portfolio Website Files

Portfolio files developed using HTML and CSS were transferred to the EC2 server.

Website Structure:

```text
website/
├── index.html
├── style.css
└── images/
```

Files were placed inside:

```bash
/var/www/html/
```

---

### Step 10: Configure Website Hosting

Existing Nginx default page was replaced with portfolio website files.

```bash
sudo cp -r website/* /var/www/html/
```

Restart Nginx:

```bash
sudo systemctl restart nginx
```

---

### Step 11: Access Website

The website became publicly accessible using:

```text
http://<EC2-Public-IP>
```

Visitors can access the portfolio directly through a web browser.

---

## Screenshots Included

The project documentation contains screenshots of:

* VPC Creation
* Subnet Creation
* Security Group Configuration
* EC2 Instance Running
* Nginx Installation
* Website Live on Browser
* GitHub Repository Structure

---

## Project Structure

```text
aws-ec2-nginx-portfolio-deployment
│
├── README.md
├|
├── screenshots
│   ├── vpc.png
│   ├── subnet.png
│   ├── securityrules.png
│   ├── ec2.png
│   ├── nginx.png
│   ├── website.png
│   └── repo.png
│
└── website
    ├── index.html
    |
    └── images/
```

---

## Learning Outcomes

Through this project, I gained hands-on experience in:

* AWS Cloud Infrastructure Setup
* VPC Networking
* EC2 Instance Management
* Linux Server Administration
* Security Group Configuration
* Nginx Web Server Deployment
* SSH Connectivity using Git Bash
* Hosting Static Websites on AWS
* Cloud Deployment Best Practices

---

## Author
Jiya Pardeshi

Cloud Application Development Trainee
This project was built as part of practical cloud deployment training to understand real-world website hosting on AWS infrastructure.
