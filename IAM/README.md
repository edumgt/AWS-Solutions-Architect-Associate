
# AWS root user
Single sign-in identity that has complete access to all AWS services and resources in the AWS account

Credentials associated with it: 
1. Email address and password (Console)
2. Access keys (AWS CLI & AWS SDK). Consist of two parts: Access key ID & Secret access key

https://aws.amazon.com/iam/features/mfa/
https://docs.aws.amazon.com/accounts/latest/reference/root-user-tasks.html
https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html
https://docs.aws.amazon.com/en_us/IAM/latest/UserGuide/id.html

Best practice:
- Activate MFA, Strogn password, Disable or delete the access keys associated with the root user, create IAM users for other tasks. 
- Create an IAM admin user once the AWS Root user has been created, and use this admin user instead of root user.

# IAM 

AWS Identity and Access Management (IAM) is an AWS service that helps you manage access to your AWS account and resources.

## IAM User 
An IAM user represents a person or service that interacts with AWS. You define the user in your AWS account. Any activity done by that user is billed to your account. When you create a user, that user can sign in to gain access to the AWS resources inside your account. When you create a user, you can provide them with credentials for Console of AWS CLI/AWS SDK

- BP: You can group IAM users and attach permissions at the group level.
- consider managing employee identity information through an identity provider (IdP). Using an IdP, whether it's with an AWS service such as AWS IAM Identity Center (successor to AWS Single Sign-On) or a third-party identity provider, provides a single source of truth for all identities in your organization. Now You can use IAM roles to provide permissions to identities that are federated from your IdP
- credentials (console, AWS CLI & AWS SDK) associated to.

## IAM Groups
An IAM group is a collection of users. All users in the group inherit the permissions assigned to the group. 
1. Groups can have many users.
2. Users can belong to many groups.
3. Groups cannot belong to groups.

## IAM role (role-based access)
IAM role is an indentiy that can be assumed by someone (external identity provider, AWS account) or something (AWS Servie) who needs temporary access to AWS Credential to perform an API call in an AWS account. 
External identity provider can be manage with AWS IAM Identity Center. 
Each IAM role comes with an ARN: Amazon Resource Name

# IAM Policies
To manage access to identities (authentication) and provide permissions (authorization) to AWS services and resources.
Least privilege is a standard security principle that advises you to grant only the necessary permissions to do a particular job and nothing more.
permission over resources with specific conditions. Permissiones are assigned to users. 

## Permissions policies 
This is a collection of permissions, mostly managed by AWS or created by users.
