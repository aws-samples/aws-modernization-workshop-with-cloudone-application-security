---
title: "Malicious FIle Upload Attack"
chapter: false
weight: 44
pre: "<b>4.4 </b>"
---


Malicious file upload is a method when invalidated files are uploaded on vulnerable servers, they can execute malicious script on the server-side to either upload phishing pages that extract users’ data, grant access to other illegal software, or gain control of the server to scrape valuable data. This policy scans for any malicious files potentially uploaded to your application, checks the file size, and blocks it based on the threshold provided by you.

---

####  If your application allows file uploads, attackers could upload malicious files that compromise your system. Application Security leverages Trend Micro™ Smart Scan as well as the Trend Micro™ Advanced Threat Scanning Engine (ATSE) to protect your application from malicious file uploads by scanning uploaded files for malware and restricting the size of uploaded files.

**1.** On your Jump-Box's desktop look for a folder name **Immersion_files** 

**2.** Inside the **Immersion_files** folder an EICAR file should already be present. If not download an EICAR sample [here](https://www.eicar.org/?page_id=3950)
![Integration](/images/eicar.png)

---

#### This time we will be proactively protecting our application. In the Application Security console, configure the policy to mitigate against **Malicious File Upload**.
![Integration](/images/file-enable.png)

#### 3. In your AWS Fargate application, choose A9 (Using Components with Know Vulnerability): 
- Lab details
- Access lab
- Click **Choose File**. Select the EICAR file under **Immersion_files** 
- Click **Upload**

![Integration](/images/file_upload_malware1.png)
![Integration](/images/file_upload_malware2.png)
![Integration](/images/file_upload_malware3.png)

---

#### 4. Upon upload the agent intervenes to block the transmission of the malicious file. 
![Integration](/images/request_blocked.png)

---

#### 5. In the Trend Micro Cloud One console, you can see the malicious file upload was blocked. Under the antivirus scanning section, you can view detailed information regarding the malware.
![Integration](/images/file-blocked.png)
![Integration](/images/file-info.png)

---

### Congrats, you just secured your first container running on AWS Fargate using Application Security!  :clap: :clap:
