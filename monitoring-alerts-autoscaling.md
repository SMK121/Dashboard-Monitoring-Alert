# Monitoring, Load Testing & Application Verification

## Overview

This exercise demonstrates deploying and testing the Tic Tac Toe application on an AWS EC2 instance.

The process included:

- Running the deployment script.
- Starting the Node.js application.
- Managing the application using PM2.
- Testing application performance using Apache Bench.
- Monitoring server performance during load testing.

---

# Deployment Script

The deployment was automated using the script:

**Script Demo TikTac.sh**

The script is used to prepare the EC2 instance and deploy the application.

The script performs:

- System package updates.
- Installation of required dependencies.
- Node.js setup.
- Application configuration.
- Application startup using PM2.
- Nginx configuration.

---

# Running the Deployment Script

Make the script executable:

    chmod +x "Script Demo TikTac.sh"

Run the script:

    ./"Script Demo TikTac.sh"

---

# Application Setup

Navigate to the application folder:

    cd ~/tech610-tic-tac-toe/app

Install application dependencies:

    npm install

Start the Node.js application:

    pm2 start index.js

Check application status:

    pm2 status

Expected result:

    status: online

---

# Nginx Verification

Check Nginx is running:

    sudo systemctl status nginx

Restart Nginx if required:

    sudo systemctl restart nginx

The application is accessed through:

    http://<EC2-Public-IP>

Nginx acts as a reverse proxy and forwards incoming traffic to the Node.js application.

---

# Apache Bench Load Testing

Apache Bench was used to simulate user traffic.

Install Apache Bench:

    sudo apt install apache2-utils -y

Run the load test:

    ab -n 1000 -c 50 http://<EC2-Public-IP>/

## Test Parameters

| Parameter | Description |
|---|---|
| -n 1000 | Total number of requests sent |
| -c 50 | Number of concurrent requests |

---

# Monitoring Performance

During load testing, server performance was monitored using:

    top

This allows monitoring of:

- CPU usage
- Memory usage
- Running processes

AWS EC2 Monitoring can also be used to view:

- CPU Utilisation
- Network activity
- Instance performance

---

# Load Test Results

Example results:

    Complete requests: 1000
    Failed requests: 0
    Requests per second: 1158
    Time per request: 43 ms

## Summary

The application successfully handled the simulated traffic load.

Results showed:

- 1000 requests completed successfully.
- No failed requests.
- Node.js application remained online.
- Nginx successfully routed traffic.
- EC2 instance remained stable during testing.

---

# Key Commands Used

    pm2 status

Checks the current application processes.

    pm2 start index.js

Starts the Node.js application.

    sudo systemctl restart nginx

Restarts the Nginx service.

    ab -n 1000 -c 100 http://<EC2-Public-IP>/

Runs a performance/load test.

    top

Monitors system resources.