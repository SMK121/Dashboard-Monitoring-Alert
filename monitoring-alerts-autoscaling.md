# Monitoring and Alerting Evidence

## Apache Bench Load Testing

Apache Bench was used to simulate user traffic against the Tic Tac Toe application to test performance under load.

Command used:

    ab -n 50000 -c 200 http://108.131.107.167/

The test generated concurrent requests and allowed CPU utilisation changes to be monitored.

Screenshot:

![<img width="1190" height="483" alt="Apache Bench Load Testing" src="https://github.com/user-attachments/assets/3e2515a3-9383-4b78-b184-eb478432b88f" />)

---

## CloudWatch CPU Monitoring

AWS CloudWatch was used to monitor EC2 CPU utilisation during the load test.

The graph shows CPU utilisation increasing during the traffic simulation and returning back towards normal levels after the test completed.

Screenshot:

![EC2 CPU Utilisation Load Test](<img width="1899" height="792" alt="EC2_CPUUtilisation_Load_Test" src="https://github.com/user-attachments/assets/b371223b-de7d-404c-9f1d-e4e342c8a8c0" />)

---

## SNS Email Subscription Confirmation

Amazon SNS was configured to send email notifications when the CloudWatch alarm was triggered.

The subscription was confirmed through the AWS SNS confirmation email.

Screenshot:

![SNS Subscription Confirmation](<img width="867" height="915" alt="AWS - Subscription Confirmation" src="https://github.com/user-attachments/assets/1c43207c-d691-4bf3-8774-ce268efc4dde" />
)

---

## CloudWatch Alarm Alert Notification

A CloudWatch CPU alarm was created and connected to the SNS topic.

When CPU utilisation exceeded the configured threshold, an email notification was received confirming the alarm entered the ALARM state.

Screenshot:

![AWS Alarm Alert Setup Confirmation](<img width="844" height="1325" alt="AWS - Alarm Alert" src="https://github.com/user-attachments/assets/e580d192-7e23-4845-af81-68bea9556343" />
)
