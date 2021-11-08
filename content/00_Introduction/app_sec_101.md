---
title: "Application Security 101"
chapter: false
weight: 12
pre: "<b>1.3 </b>"
---

## Top security risks to applications

The increasing complexity of applications and their reliance on third-party libraries, among other concerns, make them vulnerable to security risks and threats. Security professionals revealed that majority of external attacks are carried out through exploiting a software vulnerability or a web application, as stated in a 2020 Forrester report. The same report describes open-source software as a main concern in the security of applications, citing the 50% increase of open-source security vulnerabilities since last year.

---

![Benefits](/images/101-1.png)

---

The list below details the most common risks to applications that software developers should be mindful of to secure the code they produce. The Open Web Application Security Project (OWASP) Foundation has a comprehensive list of risks for web applications and APIs (WAAP). It is important that developers are aware of the most common application security risks – ones that usually result from unsecure code – so they can check the bases they need to cover at each stage of the development pipeline.

- **Using components with known vulnerabilities**: Developers use components such as libraries, frameworks, and other software modules in their applications to avoid redundant work and provide needed functionality. However, threat actors look for known vulnerabilities in these components to erode application defenses and conduct various attacks.

- **Data leaks and exposure**: Web applications that do not properly protect sensitive data could allow threat actors to steal or modify weakly protected data. They could also conduct malicious activities such as credit card fraud and identity theft, among others.  Improperly configured or badly coded APIs could also lead to a data breach.

- **Weak backend access controls** Weak back-end access controls result from improperly enforced restrictions on what authenticated users are allowed to do. Threat actors can exploit these flaws to access unauthorized functionality, which include accessing other user accounts, viewing sensitive files, modifying other user data, and changing access rights.

- **Injection**: Flaws in or improper configuration of SQL, NoSQL, OS, and LDAP can be abused in injection attacks, for example, when untrusted data is sent to a code interpreter through a form input or other data submission methods to a web application. Threat actors can use hostile data to trick the interpreter into executing malicious commands or providing unauthorized data access.

- **Security misconfiguration**: This is the most common concern for web applications. It occurs due to unsecure default configurations, misconfigured HTTP headers, incomplete or ad hoc configurations, open-cloud storage, and verbose error messages that contain sensitive information. Operating systems, libraries, frameworks, and applications should not only be securely configured to stay protected from threat actors, but also patched in a timely fashion.
Broken authentication and authorization. When application functions concerning authentication and session management are implemented incorrectly, threat actors can abuse them to compromise passwords and keys or session tokens. In turn, threat actors can hijack user or admin accounts that could be used to compromise an entire system.

- **Cross-site scripting (XSS)**: Threat actors can abuse XSS flaws to execute scripts in a browser and hijack user sessions, deface websites, or redirect the user to malicious sites. XSS flaws occur if an application includes untrusted data in a new webpage without proper validation or escaping. Such flaws could also occur if an application updates an existing webpage with user-supplied data though an HTML or JavaScript-creating browser API.

- **Unsecure deserialization**: This flaw, which is the improper conversion of serialized data back into objects that the application can use, often 
leads to remote code execution (RCE). This can also allow threat actors to perform replay, injection, and privilege escalation attacks.

- **Insufficient logging and monitoring**: Lack of capability in detecting threats could allow malicious actors to tamper, extract, or destroy data, as well as further attack systems, maintain persistence, and pivot to more systems.

---