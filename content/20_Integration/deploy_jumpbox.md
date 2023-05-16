---
title: "Deploy Jump-box"
chapter: false
weight: 31
pre: "<b>3.1 </b>"
---

## Deploy a jump-box to access application.

In order to attack our applications in this workshop. You will be submitting a sample malware file to test with. This CloudFormation template creates a EC2 to alleviate the need to disable any current anti-virus tooling.

{{% notice info %}}
<p style='text-align: left;'>
A Key Pair is required before continuing with this CloudFormation deployment. If you need help creating a Key Pair -> <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#having-ec2-create-your-key-pair" target="_top">Create a key pair</a>
</p>
{{% /notice %}}

<details>
  <summary> -> <code>CLICK HERE</code> to see how to create key pair</summary>

- In AWS navigate to **EC2**
- In the left-hand menu, under **Network & Security** select **Key Pairs**
- Click **Create Key Pair**
- Name: <code>immersion-kp</code>
- Private Key Format: **.pem**
- Click **Create key pair**
- Save the Key Pair to your local machine. It will be needed later.

![C1NS1](/images/create_kp.png) 
![C1NS1](/images/create_kp2.png) 

</details>
<br>

---

#### To deploy the jump-box click **Launch Stack**

[![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=aws-jumpbox&templateURL=https://immersionday-workshops-trendmicro.s3.amazonaws.com/application-security/app-sec-jumpbox.yml)

<details>
  <summary> -> <code>CLICK HERE</code> to see step by step instruction to deploy CFT</summary>

- Click **Next**

![C1NS1](/images/jumpbox.png)

- Leave the default parameters values, click **Next**

![C1NS1](/images/jumpbox2.png) 

- Optional: configure stack option with tags, otherwise click **Next**

![C1NS1](/images/jumpbox3.png)

- Review and click **Create Stack**

![C1NS1](/images/jumpbox4.png)
![C1NS1](/images/jumpbox5.png) 

- Wait for cloudformation deployment to complete

![C1NS1](/images/wait.png)
![C1NS1](/images/success-deployment.png)

</details>
<br>

---


![C1NS1](/images/jumpbox-architecture.png)

---

#### Access my EC2 Instance


<details>
  <summary> -> <code>CLICK HERE</code> to see step by step instruction to connect via RDP</summary>

- Navigate to **AWS EC2**
- Select instance Name: **TM-Workshop**
- Click **Connect**

![C1NS1](/images/connect.png)

- Select the **RDP client** tab
- Click **Get password**
- Click **Browse**
- Select the <code>immersion-kp.pem</code> file saved earlier
- Click **Decrypt Password**

![C1NS1](/images/connect2.png) 
![C1NS1](/images/connect3.png) 

- Copy down the **Password**
- Select **Download remote desktop file**

![C1NS1](/images/connect4.png)

- Run the RDP file to start the connection
- Click **Connect**
- Paste the decrypted **password** and click **ok**
- Click **Yes**

![C1NS1](/images/wizard.png)
![C1NS1](/images/wizard2.png)
![C1NS1](/images/wizard3.png)
![C1NS1](/images/jump-box-session.png) 


</details>
<br>
