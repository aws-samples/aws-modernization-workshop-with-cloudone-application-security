---
title: "Command Injection"
chapter: false
weight: 53
pre: "<b>5.3 </b>"
---

Remote command execution is a method when an attacker runs any malicious code of their choosing with system-level privileges on any vulnerable server. Once the server has been exploited, the attacker can gain access to all private data and information on that server. You can detect this dangerous threat by applying the detection algorithm with customized rules.

- With Remote Command Execution protection in Report mode, we can gather information regarding the vulnerability.

#### In your Lambda application command injection
- The Lambda provides a feature to perform a name server lookup on the given domain.
- Poor coding review processes can lead to exploits in an application.

![Integration](/images/lambda-rce1.png)


#### How to exploit
- <code>google.com && whoami</code>
- <code>google.com && env</code>
![Integration](/images/rce-commands.png)

#### The user can execute a command injection of arbitrary commands on the Lambda via a vulnerable application code, because of the lack of input validation.

![Integration](/images/rce-env.png)

---

#### Return to the Application Security console to gain insight into another ongoing attack.

This event is generated as **Remote Command Execution** attack.

- Check the event's **Request Details** 
- The **MITRE Attack Information** & **CWE Information** section provides additional links to understand the techniques used.
- Under **Remote Command Execution Details** you can see the execution method used:
- <code>subprocess.Popen._execute_child</code>

![Integration](/images/rce-notblocked.png)
![Integration](/images/rce-request.png)
![Integration](/images/rce-rcedetails.png)

---

#### Now that you have detected an attack, modify the policy to block subsequent remote command attacks from occurring.
- In your Application Security console, select your security group **AWS-WORKSHOP-LAMBDA**
- Configure the Remote Command Execution to **Mitigate**
![Integration](/images/remote-enable.png)

---

#### Refresh the webpage and repeat the attack with the new changes made to the agent policy. Once you attempt the exploit again, your request to the application will be intercepted and blocked. Also, in your console you are still alerted to the attack but this time it will note the Blocked action taken by the agent.
![Integration](/images/block.png)
![Integration](/images/rce-blocked.png)

---

#### Application Security offers advanced configuration for remote command attacks:
- **HTTP Params**: Application Security will detect HTTP GET or POST parameters that result verbatim into a remote command execution in a code location executed during the request.
- **Exec Control**: An algorithm that runs on each command execution within the group, comparing against the exec controls rules you’ve created. (List of rules written in REGEX)
![Integration](/images/remote-adv-config.png)
![Integration](/images/remote-adv.png)
