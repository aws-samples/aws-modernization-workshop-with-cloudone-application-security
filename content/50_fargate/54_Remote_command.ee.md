---
title: "Remote Command Execution Attack"
chapter: false
weight: 43
pre: "<b>4.3 </b>"
---

Remote command execution is a method when an attacker runs any malicious code of their choosing with system-level privileges on any vulnerable server. Once the server has been exploited, the attacker can gain access to all private data and information on that server. You can detect this dangerous threat by applying the detection algorithm with customized rules.

- With Remote Command Execution protection in Report mode, we can gather information regarding the vulnerabilityy.

#### In your AWS Fargate application, choose A1: Command Injection
- Command Injection
- Lab Details
- Access Lab
- The lab provides a feature to perform a name server lookup on the given domain.

![Integration](/images/command_injection1.png)
![Integration](/images/command_injection2.png)

#### How to Exploit
- <code>google.com && dir</code>
![Integration](/images/remote.png)

#### The user can execute a command injection of arbitrary commands on the host operating system via a vulnerable application, because of the lack of input validation.

![Integration](/images/remote-output.png)

---

#### Return to the Application Security console where you should see another ongoing attack flagged as Remote Command Execution. Under the **MITRE Attack Information** section you can follow the provided link to understand the techniques used.
![Integration](/images/remote-c1as.png)
![Integration](/images/remote-mitre.png)
![Integration](/images/remote-tech.png)

---

#### Now that you have detected an attack, modify the policy to block subsequent remote command attacks from occurring.
- •	In your **Application Security** console, select your security group “**AWS-WORKSHOP-FARGATE**”
- Configure the Remote Command Execution to **Mitigate**
![Integration](/images/remote-enable.png)

---

#### Repeat the attack. Once you attempt the exploit again, your request to the application will be intercepted and blocked. You are still alerted to the attack, but it will note the Blocked action taken by the agent.
![Integration](/images/request_blocked.png)
![Integration](/images/remote-blocked.png)

---

#### Application Security offers advanced configuration for remote command execution:
- **HTTP Params**: Application Security will detect HTTP GET or POST parameters that results verbatim into a remote command execution in a code location executed during the request.
- **Exec Control**: An algorithm that runs on each COMMAND EXECUTION within the group comparing against the exec controls rules you've created. (List of rules written in REGEX)
![Integration](/images/remote-adv.png)

