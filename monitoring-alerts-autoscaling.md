# 🎮 Tic Tac Toe AWS Deployment, Monitoring & Load Testing

## 📌 Project Overview

This project demonstrates the deployment, testing, monitoring, and alerting setup of a Node.js Tic Tac Toe application hosted on an AWS EC2 instance.

The project covers the complete deployment workflow, including:

- 🚀 Automated application deployment using a Bash script
- ☁️ AWS EC2 instance configuration
- 🌐 Nginx reverse proxy setup
- ⚙️ Node.js application deployment
- 🔄 PM2 process management
- 📊 Apache Bench load testing
- 📈 CloudWatch performance monitoring
- 🔔 CloudWatch alarms with SNS email notifications

---

# 🏗️ Architecture Overview

The application uses the following setup:

```
User
 |
 | HTTP Request
 ↓
Nginx (Port 80)
 |
 | Reverse Proxy
 ↓
Node.js Application (Port 3000)
 |
 ↓
PM2 Process Manager
 |
 ↓
AWS EC2 Instance
```

---

# 🚀 Deployment Automation

## Deployment Script

The application deployment was automated using:

**Script Demo TikTac.sh**

The script prepares the EC2 instance and configures the application environment.

The script performs:

- 🔄 System package updates
- 🌐 Installation of Nginx
- 🟢 Installation of Node.js
- 📦 Installing application dependencies
- ⚙️ Application configuration
- 🔁 Starting the application using PM2
- 🌐 Configuring Nginx reverse proxy

---

# ▶️ Running the Deployment Script

Make the script executable:

```bash
chmod +x "Script Demo TikTac.sh"
```

Run the deployment script:

```bash
./"Script Demo TikTac.sh"
```

---

# ⚙️ Application Setup

Navigate to the application directory:

```bash
cd ~/tech610-tic-tac-toe/app
```

Install application dependencies:

```bash
npm install
```

Start the Node.js application:

```bash
pm2 start index.js
```

Check the application status:

```bash
pm2 status
```

Expected result:

```
status: online
```

---

# 🌐 Nginx Configuration

Nginx was used as a reverse proxy to forward incoming web traffic to the Node.js application.

Check Nginx status:

```bash
sudo systemctl status nginx
```

Restart Nginx:

```bash
sudo systemctl restart nginx
```

Application URL:

```
http://<EC2-Public-IP>
```

Nginx receives traffic on port 80 and forwards requests to the Node.js application running on port 3000.

---

# 📊 Apache Bench Load Testing

Apache Bench was used to simulate multiple users accessing the application.

Install Apache Bench:

```bash
sudo apt install apache2-utils -y
```

Run load test:

```bash
ab -n 50000 -c 200 http://108.131.107.167/
```

## Test Parameters

| Parameter | Description |
|---|---|
| `-n 50000` | Total number of requests sent |
| `-c 200` | Number of concurrent requests |

---

# 📈 Performance Monitoring

During load testing, EC2 performance was monitored using:

```bash
top
```

This allowed monitoring of:

- CPU usage
- Memory usage
- Running processes

AWS CloudWatch was also used to monitor:

- CPU Utilisation
- Instance performance
- Resource changes during load testing

---

# 📋 Load Test Results

The application successfully handled the simulated traffic.

Example results:

```
Complete requests: 50000
Failed requests: 0
Requests per second: 1158
Time per request: 43 ms
```

Results showed:

✅ Requests completed successfully  
✅ No failed requests  
✅ Node.js application remained online  
✅ Nginx successfully handled traffic  
✅ EC2 instance remained stable  

---

# 🔔 CloudWatch Alarm & SNS Notifications

A CloudWatch alarm was created to monitor EC2 CPU utilisation.

Configuration:

- Metric: EC2 CPUUtilization
- Threshold: CPU utilisation above configured limit
- Monitoring service: AWS CloudWatch
- Notification service: Amazon SNS
- Alert method: Email notification

## Alert Workflow

```
EC2 CPU Increase
        ↓
CloudWatch Alarm Triggered
        ↓
SNS Notification
        ↓
Email Alert Received
```

---

# 📸 Monitoring & Alerting Evidence

## Apache Bench Load Testing

Apache Bench was used to generate application traffic.

Command:

```bash
ab -n 50000 -c 200 http://108.131.107.167/
```

Screenshot:

![Apache Bench Load Testing](https://github.com/user-attachments/assets/3e2515a3-9383-4b78-b184-eb478432b88f)

---

## CloudWatch CPU Monitoring

CloudWatch was used to observe CPU utilisation during the load test.

The graph shows CPU usage increasing during the test and returning towards normal levels afterwards.

Screenshot:

![EC2 CPU Utilisation Load Test](https://github.com/user-attachments/assets/b371223b-de7d-404c-9f1d-e4e342c8a8c0)

---

## SNS Email Subscription Confirmation

SNS email subscription was created and confirmed successfully.

Screenshot:

![SNS Subscription Confirmation](https://github.com/user-attachments/assets/1c43207c-d691-4bf3-8774-ce268efc4dde)

---

## CloudWatch Alarm Alert

The CloudWatch alarm successfully triggered and sent an email notification through SNS.

Screenshot:

![AWS Alarm Alert Notification](https://github.com/user-attachments/assets/e580d192-7e23-4845-af81-68bea9556343)

---

# 🛠️ Key Commands Used

## PM2 Process Management

Check application status:

```bash
pm2 status
```

Start application:

```bash
pm2 start index.js
```

---

## Nginx Management

Restart Nginx:

```bash
sudo systemctl restart nginx
```

Check Nginx:

```bash
sudo systemctl status nginx
```

---

## Application Testing

Run Apache Bench:

```bash
ab -n 50000 -c 200 http://<EC2-Public-IP>/
```

---

## System Monitoring

Monitor resources:

```bash
top
```

---

# ✅ Project Completion Summary

The Tic Tac Toe application was successfully:

✅ Deployed on AWS EC2  
✅ Managed using PM2  
✅ Exposed using Nginx reverse proxy  
✅ Tested using Apache Bench  
✅ Monitored using CloudWatch  
✅ Configured with CPU alarms  
✅ Integrated with SNS email notifications  

This project demonstrates an end-to-end AWS deployment, monitoring, and alerting workflow.
