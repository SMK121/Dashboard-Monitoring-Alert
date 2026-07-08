# Evidence Screenshots

## Application Deployment

The Tic Tac Toe application was successfully deployed on the EC2 instance and managed using PM2.

Screenshot:
- PM2 process showing the application running with status: online.

---

## Load Testing with Apache Bench

Apache Bench was used to simulate traffic against the application.

Command used:

    ab -n 50000 -c 200 http://108.131.107.167/

Screenshot:
- Apache Bench results showing completed requests and performance metrics.

---

## CPU Monitoring During Load Test

CloudWatch EC2 monitoring was used to observe CPU utilisation during the performance test.

Screenshot:
- CPU utilisation graph showing increased CPU usage during load testing and recovery afterwards.

---

## CloudWatch CPU Alarm

A CloudWatch alarm was created to monitor EC2 CPU utilisation.

Configuration:
- Metric: EC2 CPUUtilization
- Threshold: CPU utilisation greater than 8% (testing)
- Notification: SNS email alert

Screenshot:
- CloudWatch alarm configuration.
- Alarm state change notification email.

---

## SNS Email Notification

SNS was configured to send email alerts when the CloudWatch alarm entered the ALARM state.

Screenshot:
- Email confirmation.
- Alarm notification received.
