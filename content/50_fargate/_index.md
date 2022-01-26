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

#### 1.	In your [AWS account](https://aws.amazon.com/)
- Navigate to **AWS Cloud9**
- Click **Create environment**
- Name: <code>immersion-day</code>
- Click **Next step**
- Leave the default settings, click **Next step**
- Review and click **Create environment**

![cloud9](/images/cloudide1.png)
![cloud9](/images/cloudide2.png)
![cloud9](/images/cloudide3.png)
![cloud9](/images/cloudide4.png)

#### 2.	In the AWS Cloud9 IDE expand the terminal window at the bottom
- Make a directory called **aws_workshop**
- Go to **aws_workshop**
- Clone the Git repository <code>git clone https://github.com/JustinDPerkins/pygoat-tm</code>

Copy and run the commands below in Cloud9 terminal:

```
mkdir aws_workshop
cd aws_workshop
git clone https://github.com/JustinDPerkins/pygoat-tm
```

![Login](/images/git-clone.png)

---

#### 3.	Navigate into the repo home directory.
```
cd pygoat-tm
```
![Login](/images/step-2.png)

---

#### 4.	The Application Security agent uses a custom security library. You will need to edit the requirements.txt to include the package.
- Add the Application Security package to **requirements.txt**:
- In Cloud9 terminal run:

```
vi requirements.txt
```

- Type <code>i</code> and **press enter** to edit the file
- On a new line add <code>trend_app_protect</code>
- Hit the **esc** or **escape key**
- To save the changes type <code>:wq!</code>
![Integration](/images/reqs.png)

---

#### 5.	The Application Security agent needs the credentials to be able to activate successful communication to your Trend Micro Cloud One account. In your Trend Micro Cloud One account, select the tile Application Security.
![Integration](/images/c1as-tile.png)

---

#### 6.	Create a New Group named AWS-Workshop-Fargate.
- Create Group
- Note the **Key** and **Secret** to use for later.
![Integration](/images/fargate-group.png)

![Integration](/images/c1c-appsec-credentials.png)

---

#### 7.	Back in the Cloud9, under the Git project root, you need to create a file for the security library credentials.
- Create a file called <code>trend_app_protect.ini</code>
```
vi trend_app_protect.ini
```
![Integration](/images/ini-file.png)

- Here you will provide your group **Key** and **Secret** from the last steps.
- Type <code>i</code> and **press enter** to edit the file

```
[trend_app_protect]
key = 01234567-1111-2222-3333-01234567890
secret = 01234567-1111-2222-3333-01234567890
```

![Integration](/images/ini.png)

- Hit the **esc** or **escape key**
- To save the changes type <code>:wq!</code>
![Integration](/images/ini-final.png)
---

#### 8.	Last we need to import the Application Security protection module.
- Under the **root directory of the Git project that you have cloned**
```
cd pygoat/pygoat
vi wsgi.py
```

![Integration](/images/wsgi-dir.png)

- In the **WSGI** script import the **trend_app_protect.start** module
- Type <code>i</code> and **press enter** to edit the file

```
import trend_app_protect.start
```
![Integration](/images/wsgi.png)

- Hit the **esc** or **escape key**
- To save the changes type <code>:wq!</code>
- Return to the project's root directory
```
cd ~/environment/aws_workshop/pygoat-tm
```
![Integration](/images/return-to-root.png)

---

## Push to Amazon ECR repository

#### 1. Login into your [AWS account](https://aws.amazon.com/) and navigate to Amazon ECR:
- **Create a new repository**
- Visibility: **Private**
- Name: <code>aws-workshop-repo</code>
- Click **Create repository**
![Integration](/images/new-repo.png)
![Integration](/images/repo1.png)

---

#### 2. Once the repository has been created, select the new repository, and click View push commands.
![Integration](/images/select-ecr.png)

You will need these details below to push the application that you have cloned and updated with your own details:
![Integration](/images/push.png)

---

#### 3. In your Cloud9 IDE terminal, ensure you are at the root directory of the cloned Git project.
```
cd ~/environment/aws_workshop/pygoat-tm
```
![Integration](/images/root.png)

---

#### 4. Using the push commands steps provided by AWS ECR

- Retrieve an authentication token and authenticate your Docker client to your registry
- Copy the first command provided on the AWS console in the step before. It should be similar to the command in the image below:

![Integration](/images/auth.png)

---

#### 5.	Build the Docker image using the second command provided in AWS ECR console
Command: <code>docker build -t aws-workshop-repo .</code>
![Integration](/images/build.png)

---

#### 6. After the build is complete, tag your container image so you can push it to AWS ECR.

- You can use the third command command provided by AWS ECR
- Command example:**docker tag aws-workshop-fargate:latest <'account'>.dkr.ecr.<'region'>.amazonaws.com/aws-workshop-fargate:latest**
![Integration](/images/tag.png)

---

#### 7. Push the container image to your newly created Amazon ECR

- Use the fourth command provided by AWS ECR 
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
![Integration](/images/new-cluster.png)
![Integration](/images/ecs-cluster.png)

---

#### 4.	Select the **Tasks** tab, then click your **Task ID**.
![Integration](/images/ecs-cluster-task.png)

---

#### 5. Here you will be able to locate the IP address for the AWS Fargate application instance under the **Network** section.
![Integration](/images/ip-add.png)

---

#### 6. Ensure the application is working
- In our created Jump-Box, open **FireFox** and navigate to the public IP address and add <b>Port 8000</b>
    -  **Example to use in the browser:** <code>100.26.189.51:8000</code>
![Integration](/images/browser-ip.png)
![Integration](/images/pygoat.png)

---

#### Congrats, you have successfully deployed Application Security to your container applications running on Fargate. :clap: :clap: :clap: 



