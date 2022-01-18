# Systems Manager

**Overview**

1. Free service
2. Manage EC2 and On premises systems
3. Instances insights
4. Works both Windows and linux
5. Integrated with CloudWatch metrics
6. AWS Config

### **How does it work?**

Need to install agent. Comes out of the box with AMZ Linux 2 AMI and some Ubuntu AMI.Can be installed manually. Also, the instance needs proper IAM role to allow SSM actions.Fleet managed doesn’t request instances, instead the SSM Agent reaches out to fleet manager.

**Role**  should have SSM manages policy attached AmazonEC2RoleForSSM.

**SSM Documents** are used to run commands**.

1. JSON or YMAL
2. Has params
3. Has actions

Can be run as Command / Session or Automation. Can be run as fleet or resources. Integrated with IAM & CloudTrail. No need SSH. Agent sends requests instead. Can be used with EventBridge.  Output can be written in Console, sent to S3 or CloudWatch logs.

**RunCommand** gives a cli command too. Useful in cloud builds or just running aws cli from local machine.

For **Automation**, we need **Automation RunBook (automation documents)**. Automation can be triggered manually from AWS console or CLI or SDK, EventBridge, Scheduled Window and by AWS config.

**SSM Parameter Store** can be used to store configs and secrets.

1. Encryption using KMS
2. Scaleable
3. Durable
4. Easy SDK
5. Supports Versioning
6. Get notifications
7. Integrates with CloudFormation
8. Supports CloudWatch events
9. Has hierarchy

### **Get SSM Param from CLI**

`aws ssm get-parameters —names /hierarchy/of/parameter/value —with-decryption`

`aws ssm get-parameters-by-path /hierarchy/of/parameter`

`aws ssm get-parameters-by-path /hierarchy/of/parameter --recursive`

**SSM Inventory** is used for collecting metadata of (EC2/On-premises). Overview:

1. Collects metadata about software, OS drivers, config, installed updates, running services etc
2. View data in S3 or console and analyze with Athena and QuickSight
3. Metadata collection interval can be set
4. Query data from multiple AWS accounts and regions
5. Custom inventory for custom metadata

**State Manager** Automate the process of keeping managed instances (EC2/On-premises). And setup a schedule to run the task.

**Patch Manager** is used to automated patching. Supports on demand and scheduled. Reports are sent to S3. Type available are *Patch Baseline* and *Patch Group*.

**Patch Baseline** defines

1. Which patches you should and should not install on your instances.
2. Ability to create custom patch baselines. Patches can be auto-approved within days of their release
3. Only critical patches and patches related to security

### P**atch Group**

1. Associates a set of instances with a specific patch baseline
2. Can create groups for different envs
3. Instances should be defined with the tag key **Patch Group**
4. **Patch Group** can be registered with only one **Patch Baseline**

Uses document to run AWS::RunBatchBaseline .

### **Session Manager**

Start a secure shell on EC2 and On-premises servers

1. Accessing through AWS Console, AWS CLI or Session Manager SDK
2. Doesn’t need ssh, bastion hosts or SSH keys
3. Supports S3 or CloudWatch Logs
4. CloudTrail can intercept StartSession events
5. Supports linux, macOS and windows

**IM Permissions**

Control which users/groups can access Session Manager and which Instances. We can use tags to specify EC2 instances. Access SSM + write to S3 + write to cloud watch. Can restrict what commands user can run.

