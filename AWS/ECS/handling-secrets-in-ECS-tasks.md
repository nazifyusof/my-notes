# 3 Ways of Handling Secrets in AWS ECS # 

## 1. Pass secrets as environment variables in the ECS Task Definition

_Advantages_
* Minimum infrastructure needed

_Disadvantages_
* ECS Task Definition tightly coupled with secrets. A new deployment is needed if you change the value of the secret
* Secrets visible to anyone with access to the ECS Task Definition


## 2. Fetch latest secrets using an entry-point script
_Advantages_
* Secrets visible to the application only at runtime and not before that. Meaning that they are not part of the ECS Task Definition

_Disadvantages_
* The logic to fetch secrets is embedded repeatedly in different applications. So, while the secrets are (hopefully) maintained in your infrastructure configuration, each application need to know how and where to fetch them from. This violates both the DRY and Single Responsibility principles.

## 3. Use ‘valueFrom’ attribute for ECS task definition
_Advantages_
* Application doesn’t care how to fetch secrets — it expects them to be available as environment variables during run-time.
* Supports both AWS SSM Parameter Store and AWS Systems Manager (currently)

#### reference

https://faun.pub/3-ways-to-handle-secrets-in-aws-ecs-tasks-c3f4c5d688f9 