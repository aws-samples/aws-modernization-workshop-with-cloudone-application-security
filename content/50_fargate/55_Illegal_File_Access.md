---
title: "Illegal FIle Access"
chapter: false
weight: 44
pre: "<b>4.4 </b>"
---


Logging gives the ability to gain visibility into an application's activities. The log and audit trails created allow for better troubleshooting, tracking, and incident detections.
However you could become vulnerable to information leakage if you make logging and alerting events visible to a user or an attacker.

---

####  The user accessing the lab is given with a login page which says the logs have been leaked. The user needs to find the leak and try to gain the credentials that have been leaked in the logs. 

**1.** On the Pygoat application click **A10: Insufficient Logging & Monitoring**
 
 - Lab Details
 - Access Lab

 ![Integration](/images/a10.png)

**2.** Edit the application URL to display the application logs.

- <code>your.ip.address.here:8000/debug</code>

- When looking at the log we can see a get request ot the server that has a username and password to it. 
**<code>INFO "GET /a10_lab?username=Hacker&password=Hacker HTTP/1.1" 301 0</code>**

![Integration](/images/a10-1.png)


**3.** Next check the Application Security console for new events.
![Integration](/images/pygoat-ifa2.png)
![Integration](/images/pygoat-ifa3.png)


**4.** (Optional) Now you can use the credentials to log in for **A10: Insufficient Logging & Monitoring**

- Username: <code>Hacker</code>
- Password: <code>Hacker</code>


---

#### This time we will be protecting our application logs. In the Application Security console, configure the policy to mitigate against **Illegal File Access**.

![Integration](/images/pygoat-ifa.png)

#### 3. In your AWS Fargate application, refresh your web application. 

Edit the application URL to display the application logs.

- <code>your.ip.address.here:8000/debug</code>

![Integration](/images/request_blocked.png)


---

### Congrats, you just secured your first container running on AWS Fargate using Application Security!  :clap: :clap:
