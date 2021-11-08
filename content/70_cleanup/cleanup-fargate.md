---
title: "AMAZON ECS CLEANUP"
chapter: false
weight: 71
pre: "<b>7.1 </b>"
---

## Amazon ECS deployment cleanup

---

#### 1. Delete container registry
- Navigate to **Amazon ECR**
- Select your **Repository**
- Click **Delete**
- Then type delete to confirm the deletion of the Amazon ECR repository
![Integration](/images/delete-repo.png)
![Integration](/images/delete_ecs.png)

---

#### 2. Stop the cluster service
- Sign into your [AWS Account](https://aws.amazon.com/)
- Navigate to **Amazon ECS**
- Select your **cluster**
- Select **Services** tab
- Check the **Service box** and **Delete** 
![Integration](/images/ecs_deletion.png)
![Integration](/images/cancel_service.png)
![Integration](/images/service_delete.png)

---

#### 3. Stop the running AWS Fargate task.
- Select **Tasks** tab
- Check the **Task box** and **Stop** 
![Integration](/images/cancel_task.png)
![Integration](/images/task_stop.png)

---

#### 4. Delete the CloudFormation Template for the AWS Fargate workshop
- Navigate to **CloudFormation**
- Select the AWS Fargate Stack deployed
![Integration](/images/fargate-stack-delete.png)
![Integration](/images/fargate-confirm.png)

---

#### The stack will take a few minutes to delete completely.
