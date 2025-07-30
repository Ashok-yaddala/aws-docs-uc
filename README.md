# aws-docs-uc

Use Case 13: Monitoring AWS Console Login Events and Sending Notifications
Objective:
To enhance security and visibility into AWS account activity by logging all actions using AWS CloudTrail, detecting AWS Management Console login events, and sending real-time email notifications when such events occur.
Actors:
•	AWS Account Administrator
•	AWS CloudTrail
•	Amazon CloudWatch Logs
•	Amazon SNS
•	Email Recipient (e.g., Security Team or Administrator)
Preconditions:
•	AWS CloudTrail is enabled and configured to log all management events.
•	An Amazon SNS topic is created with an email subscription.
•	Necessary IAM permissions are in place for CloudTrail, CloudWatch, and SNS.
Flow of Events:
1.	Enable AWS CloudTrail:
•	Configure CloudTrail to log all management events across all regions.
•	Store logs in an S3 bucket and optionally send them to CloudWatch Logs.
2.	Detect Console Login Events:
•	CloudTrail logs events such as ConsoleLogin.
•	These logs are sent to a CloudWatch Logs group.
3.	Create CloudWatch Logs Metric Filter:
•	Define a metric filter to detect ConsoleLogin events with eventName = "ConsoleLogin" and responseElements.ConsoleLogin = "Success".
4.	Create CloudWatch Alarm:
•	Set up an alarm based on the metric filter to trigger when a login event is detected.
5.	Trigger SNS Notification:
•	Configure the alarm to publish a message to an SNS topic.
6.	Send Email Notification:
•	The SNS topic sends an email to the subscribed address with login event details.

