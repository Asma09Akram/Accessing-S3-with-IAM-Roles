# AWS Identity and Access Management

What is IAM?

Identity and Access Management is a web service which securely manage identities and access to AWS services and resources. With IAM you can control which users can access which AWS Services. 
With IAM you can choose who is authenticated(who is signed in) and who is authorized(who have permissions) to access the AWS Resources. When we create an AWS Account, the root user account gets created and it has 
complete access to all the AWS services and resources. It is a best practice is to not use root user for all the task, it is advisable to create IAM Users and start giving permissions to IAM users according to the need of Organization.


IAM Features:

* Shared access to AWS Account: With IAM you can grant access to people and services to securely share your AWS services and resources.
* Granular Permission: The permissions are fine grained as some people have acccess to few services but others may have access to single service or resources.
* Secure access to AWS resources for applications that run on Amazon EC2:


1. Click on Roles
![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/164cc5ce-0af3-4870-a584-0f087a38a85e)


2. Create a new Role
![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/ce4b44d9-0d88-473b-9980-5b44d67d6ddc)


3. Select AWS service
![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/417bf4f6-b52f-4a25-82e3-73d4b2b8adc4)


4. Choose EC2 as Use case
![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/cdcf0357-a05c-4850-9b40-ae4baa9fe377)

5. Select AmazonS3ReadOnlyAccess in Add Policy
 ![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/dd1cdfce-b4b6-47c4-a3a5-597367df34d0)

6. Give name as EC2Role

![image](https://github.com/Asma09Akram/Accessing-S3-with-IAM-Roles/assets/124654068/df307fb0-c577-430a-927e-a06e08071ae2)

7. Create Role
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

