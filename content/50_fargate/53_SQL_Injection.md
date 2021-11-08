---
title: "SQL Injection"
chapter: false
weight: 42
pre: "<b>4.2 </b>"
---

SQL injection is a method of attacking data-driven applications wherein an attacker includes portions of SQL statements in an entry field. The newly formed rogue SQL command is passed by the website to your database where it is executed. The command can result in the attacker being able to read, add, delete, or change information in the database. Application Security protects against SQL injections by blocking common SQL injection techniques.

- With SQL protection in Report mode, we can gather information regarding the vulnerability.

#### In your AWS Fargate application, choose A1: Injection
- SQL Injection
- Lab Details
- Access Lab
- This lab provides an opportunity to exploit a common SQL injection vulnerability. The application lacks input validation and exposes input into the query.

![Integration](/images/sql1.png)
![Integration](/images/sql2.png)

#### How to Exploit

````
- Username: admin
- Password: anything 1' OR '1' ='1
````

![Integration](/images/sql_injection.png)

#### In your Application Security console, you will see the agent light turn red, indicating an ongoing attack on the application. The runtime agent provides insight into the specific attack implemented as well as:
- Action taken
- Attacker source IP
- MITRE Attack information
- Trigger: The rule that triggered the SQL Injection event
- Dialect: The SQL dialect that you are using
- SQL Statement: The SQL statement that triggered the event


![Integration](/images/seceventconsole.png)
![Integration](/images/c1as-sql-report.png)
![Integration](/images/sql_mitre.png)

#### Now that you have detected an attack, let's modify the policy to BLOCK future SQL injection attacks from occurring.
- •	In your **Application Security** console, select your security group “**AWS-WORKSHOP-FARGATE**”
- Configure the SQL Injection to **Mitigate**
![Integration](/images/enable-sql1.png)

#### Go back to your AWS Fargate application and repeat the attack. Once you attempt the exploit again, your request to the application will be intercepted and blocked. Also, in your console you are still alerted to the attack but it will now note the Blocked action taken by the agent.

Here is the message that Application Security will generate when it blocks the communication:
![Integration](/images/request_blocked.png)
![Integration](/images/sql-as-block.png)

---

#### Application Security offers advanced configuration for SQL injection parameter types when you click on the right-side icon with three lines.

![Integration](/images/sql-advanced1.png)
![Integration](/images/sql-advanced.png)


