<h1>Advanced Roles and Group Management using IAM </h1>

<h2>Description</h2>
Identity and Access Management in AWS helps you securely manage and control access to AWS resources for users, through groups, roles and permissions. Roles and permissions grant or revoke authorizations to resources without any credentials. In this lab, I secured the organization's environment, using IAM policies and roles to grant and revoke S3 permissions for certain groups and users. In the final step, I verified the correct functioning of these policies utilizing the command line interface to perform operations on S3.
<br />


<h2>Languages and Utilities Used</h2>

- <b>JavaScript Object Notation</b> 

<h2>Environments Used </h2>

- <b>AWS Console</b> 
- <b>Linux Command Line Interface</b> 

<h2>Lab Walk-Through:</h2>

<p align="center">
Final Architecture : <br/>
<img src="https://github.com/TechProDavid/Files/blob/main/IAM%20security/Final%20Architecture.png?raw=true" height="90%" width="90%"/>
<br />
<br />
Creating the DevOps Group:  <br/>
<img src="https://github.com/TechProDavid/Files/blob/main/IAM%20security/Creating%20a%20group.png?raw=true" height="90%" width="90%"/>
<br />
<br/>

<p align="center">
Attaching the "Read Only" Permission to the group:
<img src="https://github.com/TechProDavid/Files/blob/main/IAM%20security/Assigning%20policies%20to%20the%20group.png?raw=true" height="90%" width="90%" />
<br />
<br />
  
<p align="center">
Creating an IAM role for EC2 instances in 2 Steps : <br/>
<img src=https://github.com/TechProDavid/Files/blob/main/IAM%20security/Attaching%20S3%20Full%20access%20permissions%20to%20EC2%20role.png?raw=true" height="90%" width="90%"/> <br/>
   Step 1: Adding the S3 full access permissions, which gives the EC2 instances full operational capabilities in S3.
  <br/>
  <br/>
<img src=https://github.com/TechProDavid/Files/blob/main/IAM%20security/Creating%20an%20IAM%20role.png?raw=true" height="90%" width="90%"/>
  <br/>
   Step 2: Name, Review and Create the policy
<br />
<br/>
  
<p align="center">
Launching the EC2 instance and creating an S3 bucket: <br/>
<br/>
<img src=https://github.com/TechProDavid/Files/blob/main/IAM%20security/Using%20the%20CLI%20to%20create%20buckets%20in%20S3.png?raw=true" height="90%" width="90%"/> <br/>
Note: The launched EC2 instance has the S3 full access permission attached to it, which allows for the successful creation and listing of the buckets, as you can see from the command line interface response from the screenshot above.

<br />
<br/>
  
<p align="center">
Verifying that the user John cannot perform S3 operations: <br/>
<br/>
<img src=https://github.com/TechProDavid/Files/blob/main/IAM%20security/verifying%20that%20user%20John%20cannot%20create%20bucket%20.png?raw=true" height="90%" width="90%"/> <br/>
Note: I logged into the Linux instance as user John, using his access and secret keys, to verify that the "read only" persmission that is attached to his group prevented him from performing S3 operations. 
  <br/>
  <br/>
As you can see from the comand line error response, the make_bucket operation "failed", because "no identity-based policy allows s3:CreateBucket action", thus confirming that the permission attached implicitely denied all S3 permissions.
