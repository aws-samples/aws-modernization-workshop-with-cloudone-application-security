---
title: "Illegal File Access"
chapter: false
weight: 54
pre: "<b>5.4 </b>"
---

Application Security protects your application against illegal file access by blocking attackers from reading or writing to your private or sensitive files.

- With Remote Command Execution protection in Report mode, we can gather information regarding the vulnerability.

#### In your Lambda application command injection
- The Lambda provides a feature to perform a name server lookup on the given domain.
- Click **Start Lab** to be taken to the lambda function

![Integration](/images/ifa-lambda.png)

---

#### How to exploit

Manipulate the browser URL using one of the options below:

- <code>https://XXXXXXX-api.ap-northeast-1.amazonaws.com/dev/ifa?file=/proc/cpuinfo</code>
- <code>https://XXXXXXX-api.ap-northeast-1.amazonaws.com/dev/ifa?file=/etc/hosts</code>
- <code>https://XXXXXXX-api.ap-northeast-1.amazonaws.com/dev/ifa?file=/proc/self/environ</code>
![Integration](/images/ifa-lambda-home.png)
![Integration](/images/ifa-url.png)
![Integration](/images/ifa-lambda-attack.png)

---

#### Check the Application Security console if any new event occurred. 

Leveraging **Request Details** (under the illegal file access event) you can see what file is trying to be accessed depending on the attack executed.

- <code>/proc/cpuinfo</code>
- <code>/etc/hosts</code>
- <code>/proc/self/environ</code>

![Integration](/images/ifa-lambda-notblocked.png)
![Integration](/images/ifa-lambda-requestdetails.png)
![Integration](/images/ifa-lambda-ifadetails.png)

---

#### Now that you have detected an attack, modify the policy to mitigate subsequent remote command attacks from occurring.
- In your Cloud One - Application Security console.
- Select your security group **AWS-WORKSHOP-LAMBDA**
- Configure the **Illegal File Access** to **Mitigate**
![Integration](/images/ifa-enable.png)

---

#### Repeat the attack with the new changes made to the agent policy.

Once you attempt the exploit again your request to the application will be intercepted and blocked. Also, in your console you are still alerted to the attack time it will note the **Blocked** action taken by the agent.

![Integration](/images/request_blocked.png)
![Integration](/images/ifa-blocked.png)

---

