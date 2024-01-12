# Monitor an EC2 Instance
## Overview
Logging and monitoring are techniques implemented to achieve a common goal. They work together to help ensure that a system's performance baselines and security guidelines are always met. 

We create an Amazon CloudWatch alarm that initiates when the Amazon Elastic Compute Cloud (Amazon EC2) instance exceeds a specific central processing unit (CPU) utilization threshold. You create a subscription using Amazon Simple Notification Service (Amazon SNS) that sends an email to you if this alarm is goes off. You log in to the EC2 instance and run a stress test command that causes the CPU utilization of the EC2 instance to reach 100 percent.
This test simulates a malicious actor gaining control of the EC2 instance and spiking the CPU. CPU spiking has various possible causes, one of which is malware.

## Environment

The lab environment includes one preconfigured EC2 instance named Stress Test with an attached AWS Identity and Access Management (IAM) role that you can use to connect via AWS Systems Manager session manager.

## Task 1: Configure Amazon SNS
![create topic](https://github.com/Cloud-Xplorer08/Monitor-EC2-Instance/assets/71820244/c65ce2f0-4f3d-4dcb-95fb-05d358f6829f)

![topic created](https://github.com/Cloud-Xplorer08/Monitor-EC2-Instance/assets/71820244/b983855c-5e51-43db-ad5c-6704d9e42f54)

![create subcription](https://github.com/Cloud-Xplorer08/Monitor-EC2-Instance/assets/71820244/21eef77f-d5b8-4b7d-ac64-53d4460673f3)

![subcription created](https://github.com/Cloud-Xplorer08/Monitor-EC2-Instance/assets/71820244/b8720880-bfc7-411f-ac66-58d470f2a1ab)


In this task, we created an SNS topic and then created a subscription for the topic by using an email address. This topic is now able to send alerts to the email address that you associated with the Amazon SNS subscription.

## Task 2: Create a CloudWatch alarm
![cpu utilization graph](https://github.com/Cloud-Xplorer08/Monitor-EC2-Instance/assets/71820244/7481d4a0-910c-4904-8748-96dfdc5df91f)

![alarm ec2 metric](https://github.com/Cloud-Xplorer08/Monitor-EC2-Instance/assets/71820244/230cd677-c0c4-431e-a5fc-08fdab90447a)

![stress test cpu utilization](https://github.com/Cloud-Xplorer08/Monitor-EC2-Instance/assets/71820244/7f8dcbca-58eb-47ef-97f3-d7b8832db6e2)

![specify metric and condition](https://github.com/Cloud-Xplorer08/Monitor-EC2-Instance/assets/71820244/2cd49b57-c3ed-4a3a-960d-2a88f778f1d7)

![condition](https://github.com/Cloud-Xplorer08/Monitor-EC2-Instance/assets/71820244/216f581f-f5ef-467c-9d6e-76a23d954062)

![configure action](https://github.com/Cloud-Xplorer08/Monitor-EC2-Instance/assets/71820244/fcbeb7a8-ebee-4cf4-becc-603c32f03fb5)

![add name an description](https://github.com/Cloud-Xplorer08/Monitor-EC2-Instance/assets/71820244/3286ef03-597d-4248-ba58-2bb897c5ab6c)

![alarm created](https://github.com/Cloud-Xplorer08/Monitor-EC2-Instance/assets/71820244/b1580084-da8a-4251-b381-3346c3749414)

In this task, we viewed some Amazon EC2 metrics within CloudWatch. You then created a CloudWatch alarm that initiates an In alarm state when the CPU utilization threshold exceeds 60 percent. 

## Task 3: Test the Cloudwatch alarm
In this task, we log in to the Stress Test EC2 instance and run a command that stresses the CPU load to 100 percent. This increase in CPU utilization activates the CloudWatch alarm, which causes Amazon SNS to send an email notification to the email address associated with the SNS topic.

![connect to EC2 instance](https://github.com/Cloud-Xplorer08/Monitor-EC2-Instance/assets/71820244/11241927-2158-4f38-89e6-b76ad9804145)

![sudo-stress](https://github.com/Cloud-Xplorer08/Monitor-EC2-Instance/assets/71820244/25fd3aca-0dbb-4752-8d62-3b560705ec7c)

![top command](https://github.com/Cloud-Xplorer08/Monitor-EC2-Instance/assets/71820244/e1fce3b4-b9f1-4801-85a0-3f5b5d130087)


In this task, you ran a command to load the EC2 instance to 100 percent for 400 seconds. This increase in CPU utilization activated the alarm to go into the In alarm state, and you confirmed the spike in the CPU utilization by viewing the CloudWatch graph. You also received a email notification alerting you of the In alarm state.

## Task 4: Create a CloudWatch dashboard

![labcpu alarm graph](https://github.com/Cloud-Xplorer08/Monitor-EC2-Instance/assets/71820244/f1da3417-1438-40ee-ba13-dc2870b22d01)

![add metric graph](https://github.com/Cloud-Xplorer08/Monitor-EC2-Instance/assets/71820244/db4304c3-0f12-4748-bda1-2ffbd1d607db)

![EC2 dashboard](https://github.com/Cloud-Xplorer08/Monitor-EC2-Instance/assets/71820244/65a5fb56-e629-4ea6-b037-2ff70bb9202d)

## Conclusion
-Created an Amazon SNS notification

-Configured a Cloudwatch alarm

-Stress tested an EC2 instance

-Confirmed that an Amazon SNS email was sent

-Created a CloudWatch dashboard



