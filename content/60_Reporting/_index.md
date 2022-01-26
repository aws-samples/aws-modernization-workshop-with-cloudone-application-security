---
title: "Reporting"
chapter: false
weight: 60
pre: "<b>6. </b>"
---

## How can security teams benefit from Application Security attack reports?

Application Security provides security teams with a consolidated view of all attacks occurring within an application. This allows your security team to give developers full visibility into how the vulnerability in their code would have been exploited, including a stack trace down to the line of code (where relevant), reporting of request parameters, and how the app’s behavior would have been modified.

{{% notice tip %}}
**VALUE:** The main dashboard displays a birds-eye view of all of your applications (requests and attacks) across all of the applications you are protecting.
{{% /notice %}}

![Integration](/images/dashboard_visibility.png)

----

## Usage tab

The usage tab provides app security teams reports on the Application Security service usage such as the number of invocations or instances protected. The usage is reported for the entire account (across all groups).

The usage is reported for the three following dimensions:

- Usage by Instance: Usage in the context of protection for serverless functions, where the licensing is based on invocation
- Usage by Invocation: Usage in the context of protection of applications running on containers or VMs/Amazon EC2s, where the licensing is based on number of containers or VMs/Amazon EC2s.
- Usage by License: Usage in the context of the application licenses, where an application license allows several containers, VMs/Amazon EC2s, and functions.


![Integration](/images/usage.png)
![Integration](/images/usage2.png)
![Integration](/images/usage3.png)

{{% notice note %}}
For more details on the usage summary view please visit the Reference section [here](https://cloudone.trendmicro.com/docs/application-security/usage/)
{{% /notice %}}

----

## Integrations Tab
The Integrations tab allows for communication channels to be configured. This allows Application Security to send event information when an attack triggers the security agent inside your application. These channels can be directed to security teams, developer teams, and operations teams so they can have insight on the type of attack and how to adjust their application accordingly.

- Slack
- PagerDuty
- New Relic Insights
- Amazon SNS

![Integration](/images/integrations.png)

---

## Example on how to integrate with Slack

#### 1. Go to [Slack](https://api.slack.com/apps)
- Select **Create an App**
- From: **Scratch**
- Give app a name
- Select workspace desired
- **Create app**
![Integration](/images/slack1.png)
![Integration](/images/slack2.png)

---

#### 2. From the side menu, select **OAuth & Permissions**
![Integration](/images/slack3.png)

---

#### 3. In the Scopes panel under Bot Token Scopes, select Add an OAuth Scope.
![Integration](/images/slack4.png)

---

#### 4. From the drop down menu:
-  Select **chat:write.public**
-  A pop-up window appears, confirming that chat:write will also be automatically added
![Integration](/images/slack5.png)

##### Here is what the scope will look like:
![Integration](/images/scope-bot.png)

---

#### 5. At the top of the page, select Install App to Workspace, then allow to workspace
![Integration](/images/slack6.png)
![Integration](/images/allow-oauth.png)

---

#### **Copy your OAuth Access Token to your clipboard.**
![Integration](/images/oauth-token.png)

---
#### 6. Navigate to your Application Security dashboard
- In the left menu, select **Integrations**
- Select **Add Integration** from the top-right corner
- Select **Slack** from the pop-up window
![Integration](/images/ints-select.png)
![Integration](/images/slack-start.png)

---

#### 7. In the Configure Slack Integration window, fill in the following fields:
- **API Key**: Your OAuth Access Token that was copied above
- **Hint**: A hint you can use to help you remember what access token was used to integrate Application Security with Slack. Your integration key will be hidden once the integration is added for security reasons
- **Channel Name**: The Slack channel you'd like the alerts to be posted to. Do not include the # sign
- **Minimum Reported Severity**: The minimum severity of alerts that you’d like to be posted to your Slack channel. You can choose between high, medium, or low. Select **LOW**
- Click **Add Integration**
![Integration](/images/slack7.png)
![Integration](/images/ints-confirm.png)

---

#### Any new attacks occurring will be pushed over to the designated Slack channel. 
![Integration](/images/slack.png)

---

#### Challenge

Return to the application deployed on AWS Fargate and perform an attack of your choice to generate your own alert!
