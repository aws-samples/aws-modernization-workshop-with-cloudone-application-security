---
title: "Managing Policy and priority"
chapter: false
weight: 15
pre: "<b>1.4.2 </b>"
---

### Policy Configuration

Each security group created has a policy attached. Policies are a collection of rules applied to your group and, therefore, your application. You can customize a policy to best suit your environment. Each protection feature can be set to either Mitigate or Report.

- **Mitigate**: Reports events and protects application with the feature's current configuration.
- **Report**: Reports events with the feature's current configuration but takes no other protection action.

Application Security supports two customizable mitigation options:

- **Block**: When a security feature applies mitigation and the mitigation type is to block, a Block page is served as a response to the user, blocking access to the application.
- **Captcha**: When a security feature applies mitigation and the mitigation type is captcha, the user is served a captcha page. If the user successfully resolves the captcha challenge, the user is allowed access to the application. Otherwise, the user keeps being presented the captcha challenge page, preventing the user from accessing the application.

![Integration](/images/policies.png)

---

### Event Priority
Event priorities are an indication of the severity of an event and the action needed on said event. The priority of an event can be found in the events table or an events details panel.

![Integration](/images/high.png)
![Integration](/images/medium.png)
![Integration](/images/low.png)

Event priorities are divided into three categories:

- **High**: Take action, configuring policies is recommended
- **Medium**: Review event, action may be needed
- **Low**: Review recommended, however action probably not needed

---
