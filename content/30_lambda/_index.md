---
title: "Vulnerable Lambda"
chapter: false
weight: 50
pre: "<b>5. </b>"
---

## How Application Security embedded agent can protect Lambda

To understand how it works better, let’s start by deploying the serverless app on your AWS environment :cloud:

---

#### 1.	Open and log into the Trend Micro Cloud One console.
Open the [Trend Micro Cloud One console](https://cloudone.trendmicro.com/) and select the Application Security tile.
![Integration](/images/c1-signin.png)
![Integration](/images/c1as-tile.png)

---

#### 2.	Create a new security group
- Click **Create New Group** 
- Group Name:  **AWS-WORKSHOP-LAMBDA**
- **Create Group**
![Integration](/images/newsecgroup.png)

---

#### NOTE: After creating the group you will be given credentials needed for the Application Security agent. 
![Integration](/images/group-config.png)

---

#### 3.	Launch the CloudFormation template provided for the Lambda application that will be deployed.
[![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=c1as-lambda-workshop&templateURL=https://aws-workshop-c1as-cft-templates.s3.amazonaws.com/c1as-vuln-serverless-app.yaml)

{{% notice note %}}
<strong>The Application Security agent has been automatically added in the CloudFormation template. The steps used to deploy the agent will be covered later in the workshop.</strong>
{{% /notice %}}

---

#### 4. Provide both the Trend Micro Cloud One [region endpoint](https://cloudone.trendmicro.com/docs/application-security/multi-regions/) and security group secret and key.
- **Stack Name:** <code>c1as-lambda-workshop</code>
- **C1RegionEndpoint:** <code>https://agents.us-1.application.cloudone.trendmicro.com/</code>
- **Security Group Key** <code>In Trend Micro Cloud One Console</code>
- **Security Group Secret** <code>In Trend Micro Cloud One Console</code>

:warning: **In our use case we are using Region US-1(US) on Trend Micro Cloud One. If you will be using a different region, please change the URL to your proper region based on the [Trend Micro Cloud One documentation](https://cloudone.trendmicro.com/docs/account-and-user-management/c1-regions/)**

![Integration](/images/cftdeploy-lambda.png)
![Integration](/images/checkiam.png)


---

#### 5.	When the stack finishes, under the OutPuts tab, obtain the website URL created.
![Integration](/images/lambda-output.png)

---

#### 6. In a new browser tab, navigate to the website URL provided to ensure app is functioning.
![Integration](/images/lambda-app-home.png)

---

{{% notice note %}}
<strong>You have successfully deployed the vulnerable serverless application on Lambda.</strong> This web app serves as learning tool and alerts you that the app is not secure, as opposed to real-world applications, which are not as illuminating.    
{{% /notice %}}
<hr>

#### Application Security provides runtime protection for serverless functions from within by providing a security layer that can be configured to protect the Lambda function. As a result, both the function code and the third-party packages leveraged by the function code are automatically protected.


Lambda provides two ways to package and deploy the serverless functions:
    
- **Functions packaged as archive** 
- **Functions packaged as container images** 

:pushpin: **For more information on Container Images to protect Lambda click [here](https://cloudone.trendmicro.com/docs/application-security/aws-lambda-with-custom-runtime-images/)**


> When Lambda functions are packaged as an archive, the runtime protection can be enabled by configuring the Lambda function to include the Application Security layer for Lambda, which contains the security algorithms that are protecting the functions.

---

## How is the agent integrated with Lambda?

Adding protection to your Lambda function is simple and only requires adding the Application Security layer and adding the required configuration for the handler and the security layer (**without any change to the function source code**). The installation and configuration are dependent on the function programming language and on the version of Amazon Linux.

---
#### Configuring the protection layer in Lambda.
- Select our previously deployed stack
- Select **Resources** tab
- Search and select the function: **IfaLambdaFunction**
![Integration](/images/lambda-resource-tabs.png)

---

#### Find the Lambda layer:

To configure the agent protection layer, you need the Amazon Resource Name (ARN) for the Application Security runtime.

- In the **Function Overview**, select **Layers** 
![Integration](/images/function-overview.png)
![Integration](/images/runtime-layer.png)

As you see above, we added the Application Security agent layer specific to Python:
    - <code>**arn:aws:lambda:<'aws region'>:800880067056:layer:CloudOne-ApplicationSecurity-python:1**</code>

{{% notice note %}}
<strong>For Lambda protection, Application Security provides support for both Python and NodeJS. See more [here](https://cloudone.trendmicro.com/docs/application-security/aws-lambda-with-official-runtimes/#arns)</strong>
{{% /notice %}}

---

#### For the Application Security layer to protect your function, some environment variables need to be added to the Lambda configuration.

To deploy the CloudFormation template, these parameters are required for a successful agent connection.

- On the **IfaLambdaFunction** overview page, select the **Configuration tab** 
- Select **Environment variables**
![Integration](/images/func-configs.png)
![Integration](/images/variables.png)

{{% notice note %}}
For advanced Lambda configuration please see our documentation [here](https://cloudone.trendmicro.com/docs/application-security/aws-lambda-with-official-runtimes/#additional-configuration-for-lambda-on-aws-official-runtimes)
{{% /notice %}}

#### Navigate back to the website URL and refresh the page a few times to allow the agent to activate for the first time.
- Go to your Application Security Console
- To determine if agent is active, use the indicator light next to the **security group**

#### **Inactive** (White or grey light)
- **White:** Not Connected
- **Grey:** Inactive
![Integration](/images/inactive.png)

#### **Active** (Red, green or yellow light)
- **Red:** Connected with ongoing attack
- **Yellow:** Connected with previous attacks in last hour
- **Green:** Connected with no attacks currently  
![Integration](/images/active.png)

{{% notice note %}}
<strong>The Lambda function will only show as active when it is being used or triggered to process an event. The status light will be remain inactive (grey) until a request is made, triggering the Application Security agent</strong>
{{% /notice %}}

---
#### Congrats 🎉 you have successfully deployed Application Security to your Lambda. :laptop: :cloud: :rocket:
