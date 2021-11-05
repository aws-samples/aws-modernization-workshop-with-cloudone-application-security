---
title: "Configuring Security Policy"
chapter: false
weight: 41
pre: "<b>4.1 </b>"
---

### Protect your application with Application Security
---
 
#### 1.	Open the Trend Micro Cloud One console and [log in](https://cloudone.trendmicro.com). 
![Integration](/images/c1-signin.png)

---

#### 2.	Select the Application Security tile.
![Integration](/images/c1as-tile.png)

---

#### 3.	Select the **AWS-WORKSHOP-FARGATE** security group created previously and edit the policy.
- Ensure all modules are **ENABLED**
- Ensure all modules are in **REPORT** mode.
- **Save**
![Integration](/images/policy-setup-fargate.png)
![Integration](/images/starting-fargate.png)

---

#### 4.	Open your AWS management console and [log in](https://aws.amazon.com/).
- Navigate to **Amazon ECS**
- Select our created **Cluster**
- Select **Tasks** Tab
- Select your **Task ID** to obtain the **Public IP address**
- Navigate to a new browser tab to add: **your.ip.address:8000**
![Integration](/images/pygoat.png)

---

#### 5. Create a fake user and log in with the user created
Example:

- Username: <code>aws-workshop</code>
- Password: <code>L3tsL3arn!</code>
![Integration](/images/sign-up.png)
![Integration](/images/new_user.png)
![Integration](/images/login_pygoat.png)

**Now let's start the attacks tests :laptop: :rocket:**
