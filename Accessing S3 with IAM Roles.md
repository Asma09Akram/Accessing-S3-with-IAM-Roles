# AWS Identity and Access Management

What is IAM?

Identity and Access Management is a web service which securely manage identities and access to AWS services and resources. With IAM you can control which users can access which AWS Services. 
With IAM you can choose who is authenticated(who is signed in) and who is authorized(who have permissions) to access the AWS Resources. When we create an AWS Account, the root user account gets created and it has 
complete access to all the AWS services and resources. It is a best practice is to not use root user for all the task, it is advisable to create IAM Users and start giving permissions to IAM users according to the need of Organization.

There are two important types of policies:
**Identity-Based-Policies**
They are attached to an IAM user, group, or role. These policies will tell what all permissions the user, group or role have. For example, you can attach the policy to the IAM user named Asma, stating that she is allowed full access to the Amazon EC2 Instances action. 

**Resource-Based-Policies**
They are attached to a resource. For example, you can attach resource-based policies to Amazon S3 buckets, Amazon SQS queues, VPC endpoints etc. With resource-based policies, you can specify who has access to the resource and what actions they can perform on it.

**IAM Role**

An IAM role is an IAM identity that you can create in your account that has specific permissions. An IAM role is similar to an IAM user, in that it is an AWS identity with permission policies that determine what the identity can and cannot do in AWS. However, instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it. Also, a role does not have standard long-term credentials such as a password or access keys associated with it. Instead, when you assume a role, it provides you with temporary security credentials for your role session.

Lets Do Hands-On to Access S3 Bucket with IAM Role.

Pre requisites: Create an S3 bucket with the name "s3bucket-17-1-2024"


## Task 1. Create IAM Role and attach policy to it

1.1 Go to IAM in the Security, identity, & Compliance section. Click on Roles present under left navigation menu.

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/164cc5ce-0af3-4870-a584-0f087a38a85e)


1.2. Create a new Role

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/ce4b44d9-0d88-473b-9980-5b44d67d6ddc)


1.3. Select AWS service

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/417bf4f6-b52f-4a25-82e3-73d4b2b8adc4)


1.4. Choose EC2 as Use case

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/cdcf0357-a05c-4850-9b40-ae4baa9fe377)

1.5. Select AmazonS3FullAccess in Add Policy
  
1.6. Give name as EC2Role

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/df307fb0-c577-430a-927e-a06e08071ae2)

1.7. Create Role

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/eac7ed2c-6a22-4aeb-bca1-1dc7fe81ea1b)


### Task 2: Launch an EC2 Instance

2.1 Go to Services menu in the top, then click on EC2 in the Compute section, Click on Instances from the left side bar and then click on Launch instances button.
Name : Enter EC2 Server

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/ead4e612-7e44-4f05-a6fc-337177d5a3c5)

2.2 Choose Amazon Linux 2

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/a669c670-e41c-443a-8994-7b07d8b18fd0)

2.3 Instance type as t2.micro

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/b93cc731-59b1-41e0-8e19-bffb15f0aae7)

2.4 Create a new Key Pair as EC2 keypair

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/46f55109-ca87-431a-9c0c-e5799ed9e6b4)

2.5 Create a new Security Group, 
Security group name : Enter S3server-SG
Description : Enter Security Group to allow traffic to EC2

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/1390ce3c-9f36-4140-acb8-eabbb7c005be)

2.6 To add SSH
Choose Type: Select SSH 
Source: Select Anywhere

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/2a2ed991-a673-458d-81c5-6c7181ed246f)

2.7 Under Advanced Details
Choose Role as EC2Role

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/66cd906d-47f0-45f0-9d63-6c4ce0f60e76)

2.8 Keep remaining things same and click on Launch Instance

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/2311ddd7-53e5-4198-8164-880acb4a16ad)


### Task 3. Connect EC2 Instance

3.1 Click on EC2 Server and click on Connect Button

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/307bc808-b006-4932-bf3c-7c76b0d6633a)

3.2 Go to EC2 Instance Connect and click on Connect

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/49c4583c-65c7-4e70-b62f-2408c57b6d09)

3.3 After connection is established 
type the command
switch to the root user: **sudo su**

```aws s3 ls``` this will list all the buckets in your account, here in this case with the help of EC2 Role, S3 bucket is accessed by EC2 Instance. Ec2 instance has assumed the role and it is able to read the S3 bucket.

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/27a51e71-3fc1-4a88-ac57-7531b387b4bc)

3.4 Lets create a new file 
```touch test1.txt```


![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/eb5ae065-287c-43df-b451-18ea84d6e0fb)

3.5 Now upload it to the bucket via AWS CLI (using the following set of commands):
```aws s3 mv test1.txt s3://s3bucket-17-1-2024  ```
![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/22a4e683-dc91-4f83-a058-95c2943e211d)

3.6 Check for the new file in the S3 bucket.

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/b2391f09-a750-4702-8e35-5bdcc8e321d7)

3.7 Create some files like test2.txt, test3.txt and upload to s3 bucket

3.8 You can also list the files uploaded to S3 bucket via CLI from the EC2 instance with the following command:

```aws s3 ls s3://s3bucket-17-1-2024```

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/f3afed2a-dfe3-4190-b917-409a41b6ba1a)


## Task 4. Clean up all the resources 

4.1 Go to EC2 Instance and Select the EC2 Server and Click on Instance State and Terminate Instance

4.2 Go to S3, click on the bucket which you have created earlier and click on the file in S3 bucket and click on delete. Delete the files first and then go to the bucket and click on Delete, thats how you will be able to delete the bucket.


