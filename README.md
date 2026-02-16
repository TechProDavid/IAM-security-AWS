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
Final Architecture after encryption: <br/>
<img src="https://github.com/TechProDavid/Files/blob/main/Cloud%20Environment%20-%20after%20encryption.png?raw=true" height="80%" width="80%" alt="Architecture"/>
<br />
<br />
Creating the Customer Managed Key:  <br/>
<img src="https://github.com/TechProDavid/Files/blob/main/S3%20&%20Bucket%20Policy%20lab%20(9).png?raw=true" height="80%" width="80%" alt="Architecture"/>
<img src="https://github.com/TechProDavid/Files/blob/main/S3%20and%20Bucket%20Policy%20lab%20(4).png?raw=true" height="80%" width="80%" alt="Architecture"/>
<br />
<br />
Editing the key policy in JSON format: <br/>
<img src="https://github.com/TechProDavid/Files/blob/main/S3%20and%20Bucket%20Policy%20lab%20(5).png?raw=true" height="80%" width="80%" alt=""/>
<br />
<br />
Editing the S3 Bucket policy to deny the upload of files that are unencrypted:  <br/>
<img src="https://github.com/TechProDavid/Files/blob/main/S3%20and%20Bucket%20Policy%20lab%20(2).png?raw=true" height="80%" width="80%" alt="Architecture"/>
<br />
## The condition portion of the policy at the bottom expresses that server-side-encryption needs to be within AWS:KMS. But since the overall policy's "Effect" is "Deny", any object that was not encrypted with AWS KMS sever side encryption would not get uploaded into this bucket.
<p align="center">
Re-editing the policy to use only the customer managed key:  <br/>
<img src="https://github.com/TechProDavid/Files/blob/main/S3%20&%20Bucket%20Policy%20lab%20(8).png?raw=true" height="80%" width="80%" alt="Architecture"/>
<br />
## I edited the policy a second time to be more specific about the encryption requirements and narrow it down to the CMK that was created in the first step
<br />
<br />
<p align="center">
Verifying failed upload of unencrypted file: <br/>
<img src="https://github.com/TechProDavid/Files/blob/main/Verifying%20unencrypted%20policy.png?raw=true" height="80%" width="80%" alt="Architecture"/>
<br />
<br />
<p align="center">
Uploading a file using the key created:<br/>
<img src="https://github.com/TechProDavid/Files/blob/main/S3%20&%20Bucket%20Policy%20lab%20(7).png?raw=true" height="80%" width="80%" alt="Architecture"/>
<br />
<br />
Confirming successful upload of encrypted file: <br/>
<img src="https://github.com/TechProDavid/Files/blob/main/Verifying%20that%20policy%20works%20for%20encrypted%20files.png?raw=true" height="80%" width="80%" alt="Architecture"/>
