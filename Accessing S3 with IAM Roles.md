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


