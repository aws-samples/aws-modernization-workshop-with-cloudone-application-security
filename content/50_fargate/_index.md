---
title: "Vulnerable Container Application"
chapter: false
weight: 40
pre: "<b>4. </b>"
---

## How can Application Security protect containers?

Now we will be showing how Application Security can protect microservices applications running on AWS Fargate.

{{% notice tip %}}
This application is written in Python 3.8. Following the Trend Micro documentation found [here](https://cloudone.trendmicro.com/docs/application-security/python/), we will integrate Application Security to protect our application before pushing our container image to AWS ECR.
{{% /notice %}} 

---

#### 1.	Navigate to [Github page](https://github.com/JustinDPerkins/pygoat-tm) and clone the repository on your local machine
- Make a directory called **aws_workshop**
- Go to **aws_workshop**
- Clone the Git repository **https://github.com/JustinDPerkins/pygoat-tm**

Here are the example of Linux and Mac commands to do the steps mentioned:

```
mkdir aws_workshop
cd aws_workshop
git clone https://github.com/JustinDPerkins/pygoat-tm
```

![Login](/images/github.png)
![Login](/images/git-clone.png)

---

#### 2.	In a Command/Terminal/Shell window navigate into the repo home directory.
```
cd pygoat-tm
```
![Login](/images/step-2.png)

---

#### 3.	The Application Security agent uses a custom security library. You will need to edit the requirements.txt to include the package.
- Add the Application Security package to **requirements.txt**:
- <code>trend_app_protect</code>
![Integration](/images/reqs.png)

---

#### 4.	The Application Security agent needs the credentials to be able to activate successful communication to your Trend Micro Cloud One account. In your Trend Micro Cloud One account, select the tile Application Security.
![Integration](/images/c1as-tile.png)

---

#### 5.	Create a New Group named AWS-Workshop-Fargate.
- Create Group
- Note the **Key** and **Secret** to use for later.
![Integration](/images/fargate-group.png)

![Integration](/images/c1c-appsec-credentials.png)

---

#### 6.	Back in the terminal window, under the Git project root, you need to create a file for the security library credentials. Follow the steps-by-steps below to make the configuration:
- Create a file called <code>trend_app_protect.ini</code>
- Provide your group **Key** and **Secret**
![Integration](/images/ini-file.png)
![Integration](/images/ini.png)

---

#### 7.	Next, we need to import the Application Security protection module.
- Under the **root directory of the Git project that you have cloned**
- <code>cd pygoat/pygoat</code>
- Import the **trend_app_protect.start** module at the top of your **WSGI** script
- <code>import trend_app_protect.start</code>
- **Save** return back to the **Git project root directory**
![Integration](/images/wsgi-dir.png)
![Integration](/images/wsgi.png)

---

## Push to Amazon ECR repository

#### 1. Login into your [AWS account](https://aws.amazon.com/) and navigate to Amazon ECR:
- **Create a new repository**
![Integration](/images/new-repo.png)
![Integration](/images/repo1.png)

---

#### 2. Once the repository has been created, select the new repository, and click View push commands.
![Integration](/images/select-ecr.png)

You will need these details below to push the application that you have cloned and updated with your own details:
![Integration](/images/push.png)

---

#### 3. In a terminal/shell/command window, navigate to the root directory of the previously cloned Git project.
![Integration](/images/root.png)

---

#### 4. Using the push commands steps provided by AWS

{{% notice warning %}}
<p style='text-align: left;'>
Before pushing the container image to Amazon ECR, you need to have the <b>AWS CLI configured</b>. If you need help, use the <a href="https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html" target="_top"><b>link here.</b></a> 
</p>
{{% /notice %}}


{{% notice warning %}}
<p style='text-align: left;'>
It's important to remember that you need to have Docker installed on your desktop to run this lab. For more details how to install <b>Docker into your desktop</b>, click the <a href="https://docs.docker.com/desktop/" target="_top"><b>link here.</b></a>  
</p>
{{% /notice %}}

- Retrieve an authentication token and authenticate your Docker client to your registry
    -  Use the first command provided on the AWS console in the step before. It should be similar to the command in the image below:

![Integration](/images/auth.png)

---

#### 5.	Build the Docker image using the second command provided in AWS console
Command: <code>docker build -t aws-workshop-repo .</code>
![Integration](/images/build.png)

---

#### 6. After the build is complete, tag your container image so you can push it to this container image registry.

- You can use the third command provided in the previous steps on the AWS console:
- Command example:**docker tag aws-workshop-fargate:latest <'account'>.dkr.ecr.<'region'>.amazonaws.com/aws-workshop-fargate:latest**
![Integration](/images/tag.png)

---

#### 7. Push the container image to your newly created Amazon ECR

- You can use the fourth command provided in the previous steps on the AWS console 
- Command example:**docker push <'account'>.dkr.ecr.<'region'>.amazonaws.com/aws-workshop-fargate:latest**
![Integration](/images/push1.png)

---

#### 8. Check if the container image was push with success to Amazon ECR
- In AWS console, navigate to Amazon ECR
- Select your repository name
- Copy the latest image tag: **Image URI**
![Integration](/images/uri.png)

---

## Deploy the AWS CloudFormation template provided to deploy the Amazon ECS infrastructure.
{{% notice note %}}
This AWS CloudFormation template creates a VPC with internet access and two public subnets, an Amazon ECS cluster, and a task definition pointing towards the Amazon ECR repository created in the previous steps 
![Integration](/images/fargate-archi.png)
{{% /notice %}}

[![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=c1as-fargate-workshop&templateURL=https://aws-workshop-c1as-cft-templates.s3.amazonaws.com/c1as-fargate-workshop.yaml)

---

#### 1. Name the stack and provide the image URL.
![Integration](/images/config-ecs-stack.png)
![Integration](/images/checkiam.png)

---

#### 2. View your template Outputs to obtain cluster name, VPC ID, and security group.
![Integration](/images/fargate-outputs.png)

---

#### 3. Navigate to Amazon ECS and select the newly created cluster.
![Integration](/images/ecs-cluster.png)

---

#### 4.	Select the **Tasks** tab, then click your **Task ID**.
![Integration](/images/ecs-cluster-task.png)

---

#### 5. Here you will be able to locate the IP address for the AWS Fargate application instance under the **Network** section.
![Integration](/images/ip-add.png)

---

#### 6. Ensure the application is working
- In a new browser tab, navigate to the public IP address and add <b>Port 8000</b>
    -  **Example to use in the browser:** 100.26.189.51:8000
![Integration](/images/browser-ip.png)
![Integration](/images/pygoat.png)

---

#### Congrats, you have successfully deployed Application Security to your container applications running on Fargate. :clap: :clap: :clap: 



