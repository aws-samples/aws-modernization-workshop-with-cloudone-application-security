---
title: "Introduction"
chapter: false
weight: 10
pre: "<b>1. </b>"
---

## The State of Application Security in Cloud Infrastructure

With the accelerated shift to the cloud, enterprises are subsequently accelerating their development processes to maximize operational excellence. In order to efficiently handle customer and security needs, businesses are relying on container and serverless technologies for their scalability and cost-effectiveness when deploying and developing applications.


Containers and serverless technology may already be a central part of your arsenal, so you might be wondering: “what does this have to do with me?” Well, as with any burgeoning technology, container-based and serverless applications are not immune to risks and threats. It is only a matter of time before malicious actors, who are always casting wider nets to reach more potential victims, start frequently targeting them for various schemes. This means you must find a way to implement the appropriate defense measures to save yourself and your enterprise from post-deployment headaches like attacks, fines, and distrust from customers.


This workshop focuses on specific security considerations for developers and how they can build the best defense for container-based and serverless applications through runtime application self-protection (RASP), a tool that incorporates security into an application at runtime.


---

### What is RASP?

RASP represent a set of security controls and capabilities embedded with the web application and protecting the application from within. RASP can protect applications from attacks by analyzing both an application’s behavior as well as the context of that behavior. Part of the embedded protection DNA in Application Security is inherited from RASP and thus Application Security shares the same benefits as RASP.

---

### How Application Security can benefit application

In essence, RASP provides real-time protection to applications. RASP can intercept all kinds of traffic that indicate malicious behavior like SQL injection, cross-site scripting (XSS), vulnerabilities, bots, and attacks deployed through email, Slack, and other message types.


Because RASP is embedded within the web application, it is innately capable of monitoring application behavior. Thus, RASP can prevent attacks with high accuracy as it can discern between attacks and legitimate requests, reducing false positives and allowing security engineers to focus on combatting more serious problems.


In addition, RASP also offers better protection from zero-day exploits. RASP offers a short-term fix if a patch for an application is not readily available for an extended period. The agent not only protects the vulnerabilities introduced in the application code itself but also for vulnerabilities in 3rd party libraries leveraged. To add, RASP is not dependent on any type of signature for an exploit because the baseline for proper operation is the application itself.


---

## What is Serverless?

“Serverless” is a bit of a misnomer. Applications run on a third-party cloud infrastructure, such as Lambda. They don’t rely on a dedicated server, virtual machine, or container; only the application’s code runs on a cloud server until it completes its task.


Serverless applications embody the budding function-as-a-service (FaaS) model, turning cloud computing into a platform that enterprises can use to develop, deploy, and manage their applications without having to set up the necessary infrastructure.


By going “serverless,” developers and enterprises benefit from flexibility and automation. It can also be a scalable and cost-effective way to launch applications as there is no need to provision or maintain dedicated servers or install and manage software or runtime.


---- 

## What are the most prevalent security issues in serverless apps?

- Data injection — in this case, untrusted or unsanitized inputs relayed between an application’s components, such as storage, database, and notification systems
- Insufficient monitoring and logging capabilities
- Permissions that an application requests or grants
- Misconfigured authorization settings in cloud storages
- Authentication mechanisms
- Unsecure code from third-party packages


---- 

## What is the impact of these security issues?

These security issues can allow hackers to manipulate applications and carry out malicious actions. Web injections such as SQL injection and XSS attacks, for instance, can allow an attacker to gain administrator-level privileges to the application’s database. Misconfigured cloud storage can expose stored personal or mission-critical data to cybercriminals.


Weak authentication and authorization mechanisms can be exploited to execute man-in-the-middle attacks that can let hackers steal personally identifiable information. A serverless application with no security event logging and monitoring features significantly reduces the developer and organization’s capability to respond proactively to incidents such as data breaches and malware attacks.

---- 

## How do we make sure that we are fulfilling our responsibility?

Adopting the shared responsibility model is key to securing these services as it requires both the cloud service provider (CSP) and the user to maintain areas of responsibility to keep their computing environment protected

![infographic](/images/Shared_Responsibility_Mode.jpg)

While running an application in a serverless environment can significantly reduce the operational overhead and security impact on the company, it does not eliminate them. This is especially true for threats that take advantage of vulnerabilities and poor coding practices.

---- 
