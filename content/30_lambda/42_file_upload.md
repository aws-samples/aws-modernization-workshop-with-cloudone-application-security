---
title: "Malicious File Upload"
chapter: false
weight: 52
pre: "<b>5.2 </b>"
---


Malicious file upload is a method when invalidated files are uploaded on vulnerable servers, they can execute malicious script on the server-side to either upload phishing pages that extract users’ data, grant access to other illegal software, or gain control of the server to scrape valuable data. This policy scans for any malicious files potentially uploaded to your application, checks the file size, and blocks it based on the threshold provided by you.

---

#### If your application allows file uploads, attackers could upload malicious files that compromise your system. 

Application Security leverages Trend Micro Smart Scan as well as the ATSE to protect your application from malicious file uploads by scanning uploaded files for malware and restricting the size of uploaded files.

**1.** Go to [EICAR](https://www.eicar.org/?page_id=3950) and obtain the test file developed for a simple test of anti-malware engine.

:warning: **Temporarily disable your virus scanner, otherwise it will catch the eicar file and delete it.**

**2.** Create a **.txt** file containing the EICAR string.
![Integration](/images/eicar.png)

---

#### Currently the agent’s security policy is set in report mode.
![Integration](/images/setup-policy.png)


#### 3. In your application, choose Malicious File Upload: 
- Select the EICAR file saved
- Submit
![Integration](/images/lambda-mfu.png)
![Integration](/images/success-upload.png)

---

#### 4. Check the Application Security dashboard for any events.
![Integration](/images/mfu-reported.png)

---

#### 5. From the above image, two different threat types were identified. 
- Select the **Illegal File Access** to display additional details.
- Examine the **Request Details** and **Illegal File Access Details**
![Integration](/images/lambda-mfu-ifa-1.png)
![Integration](/images/lambda-mfu-ifa-2.png)

---

#### 6. Make an exception in the policy under Illegal File Access
- Select **AWS-WORKSHOP-LAMBDA** -> **Policies** 
- **Configure Policy**
- Select tab **Read Controls**
- **Add Rule**
- <code>/var/runtime/botocore/data/*</code>
- **Submit Rule** and **Save Changes**

![Integration](/images/ifa-exception.png)
![Integration](/images/readcontrols.png)
![Integration](/images/rule.png)

---

#### 7. Select the Malicious File Upload event to see the details of the request.
![Integration](/images/mfu-notblocked.png)
![Integration](/images/mfu-requestdetails.png)
![Integration](/images/mfu-scandetails.png)


---

#### 8. Change the Malicious File Upload mode to Mitigate.

![Integration](/images/mfu-mitigate.png)

---

#### 9. Navigate back to the website URL and refresh the webpage. Repeat the eicar file upload process.

![Integration](/images/block.png)
---

#### 10. In the Trend Micro Cloud One console, you can see the malicious file upload was blocked. Under the Antivirus scanning section, you can view detailed information regarding the malware.
![Integration](/images/mfu-blocked.png)
![Integration](/images/file-info.png)

---

#### Congrats, you have implemented a security measure to prevent malicious objects from being uploaded to downstream workflows and you also created a read exception in policy!  :clap: :clap: