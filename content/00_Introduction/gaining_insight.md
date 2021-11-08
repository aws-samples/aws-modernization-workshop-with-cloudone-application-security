---
title: "Gaining Insight"
chapter: false
weight: 14
pre: "<b>1.4.1 </b>"
---

### Dashboard Visibility for Your Applications

Application Security organizes your applications by security groups. A security group is a collection of web applications and/or serverless functions sharing a common set of policies. The security group can include multiple instances of an application, multiple applications, and/or serverless functions.


Here you will see the security group for your Fargate application with the Application Security agent deployed. The Application Security agent inspects every request submitted to your application and executes the security checks as specified by your policy. An event is triggered when a security threat occurs and triggers a rule in your policy.


The Application Security real time events chart and table provides a visual representation of the number of requests or invocations inspected and protected by the Application Security agent, as well as the collection of security events triggered by the Application Security agent from all of your groups.


---

#### Events Chart

- **REQUESTS**: The number of requests or invocations inspected and protected by the Application Security agent. The scale of the number of requests is shown on the left of the chart.
- **EVENTS**: The collection of security events triggered by the Application Security agent, from all your groups. The scale of the number of events is shown on the right of the chart.

![Integration](/images/dashboard_visibility.png)

#### Events Table

The events table lists the most recent events and when it’s selected, it will display information relating to every type of event including:

- **Attack Type**
- **Affected Group**
- **Action taken**
- **Attacker IP**
- **Request details**
- MITRE attack information

Note: every event includes the request details panel for general information about the event

![Integration](/images/event-details.png)

#### MITRE

The MITRE Attack information panel displays MITRE Attack identification numbers and links to the MITRE website. The attack ID is related as closely as possible to the vulnerability that triggered the event. Here is a Knowledge Base link to gain further insight on technique used.

#### Attack Details

At the bottom of the Event Details panel will be information regarding the specific attack. In this case, under **Illegal File Access Details**, the following information is displayed:

![Integration](/images/general-details.png)

---

#### Stack Trace Detail

In addition to providing the event details as shown, you can click **View Stack** to see the full stack trace of the specific event selected. In this example we show an illegal file access event stack trace.

![Integration](/images/event-details-stack.png)
![Integration](/images/trace-stack.png)

---

### Understanding Application Security

Determined attackers are continuously running scanners against your site, creating malicious user accounts, fuzzing various elements, triggering exceptions, and attempting to run exploitation tools. Attackers do this to:

- steal sensitive data stored on your servers
- take over customer or administrative accounts
- execute code on your server

By including Application Security in your applications, you will receive alerts as soon as attackers begin conducting scans and attacks. You can address each event manually, or you can configure Application Security to react automatically to these attackers, stopping them in their tracks before any damage is done.​

Most importantly, real vulnerabilities are not exploited because of the runtime protection, and your developers will have code-level information regarding the vulnerability.

---

![Integration](/images/coverage.png)

---

