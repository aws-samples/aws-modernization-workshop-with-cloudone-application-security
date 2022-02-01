---
title: "Configuring Security Policy"
chapter: false
weight: 51
pre: "<b>5.1 </b>"
---

## How Application Security can protect your Lambda function application

#### 1.	Open your AWS management console and log into [AWS](https://aws.amazon.com/).
- Navigate to **CloudFormation**
- Select our **Deployed Stack**
- Select **Outputs** Tab
- Locate your **website URL**
- Navigate in new browser tab to the stack provided URL
![Integration](/images/lambda-output.png)
![Integration](/images/lambda-app-home.png)

#### 2.	Open the Trend Micro Cloud One console and [log in](https://cloudone.trendmicro.com). 
![Integration](/images/c1-signin.png)

#### 3.	Select the Application Security tile.
![Integration](/images/c1as-tile.png)

#### 4.	Select the **AWS-WORKSHOP-LAMBDA** security group created previously and edit the policy.
- •	Click on the icon with the 3 lines, this will open the security policy configuration 
- Ensure the following modules are **ENABLED**
- Ensure the enabled modules are in **REPORT** mode.

The finshed policy should look like below:

![Integration](/images/setup-policy.png)

---

#### Congrats, you just configured your first Lambda function policy using Application Security!