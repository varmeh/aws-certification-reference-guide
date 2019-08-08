- [Identity Access Management](#identity-access-management)
  - [What is IAM](#what-is-iam)
  - [How IAM works](#how-iam-works)
  - [Identities](#identities)
    - [Users](#users)
      - [Root User](#root-user)
      - [Password Policy](#password-policy)
      - [Multi-Factor Authentication](#multi-factor-authentication)
    - [Groups](#groups)
    - [Roles](#roles)
      - [Temporary Security Credentials](#temporary-security-credentials)
  - [Policies](#policies)
    - [Managed and Inline Policies](#managed-and-inline-policies)
    - [Identity vs Resource Based Policies](#identity-vs-resource-based-policies)
    - [Roles vs Resource based policies](#roles-vs-resource-based-policies)
    - [Policy Evaluation Logic](#policy-evaluation-logic)
  - [IAM Best Practices](#iam-best-practices)

# [Identity Access Management](https://aws.amazon.com/iam/)

## [What is IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)

- IAM is a web service that helps you securely control access to AWS resources
- You use IAM to control who is authenticated (*signed in*) and authorized (*has permissions*) to use resources

## [How IAM works](Understanding How IAM Works)

<!-- Section Demarkation -->
## [Identities](https://docs.aws.amazon.com/IAM/latest/UserGuide/id.html)

- Refer to resources which you create to provide authentication for people & process in AWS
- Each of these can be associated with one or more policies to determine what actions could they do, with which AWS resources and under what conditions (*defined in policies*)
- 3 identities in AWS:
  - Users
  - Groups
  - Roles

- [**Tagging**](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_tags.html): You could tags to a User or Role which could then be used to control access to resources

<!-- Sub-Section Demarkation -->
### [Users](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction_identity-management.html)

- An entity that you create in AWS to represent the person or application that uses it to interact with AWS
- A user in AWS consists of a name and credentials
- New users have *NO PERMISSIONS* when first created
- User *Access Key Id* & *Secret Access Key* are used to access AWS via API or CLI

- **User Access Keys**: 
  - Use access keys to sign programmatic requests to the AWS CLI or AWS API
  - It DOESNOT work on AWS Console. Use user login credentials to access Console
  - It has 2 parts:
    - **An Access Key ID**
    - **A Secret Access Key**

#### [Root User](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html)

- When you first create an AWS account, you begin with a single sign-in identity that has complete access to all AWS services and resources in the account. This identity is called the AWS account *root user*
- Don't use your AWS account root user credentials to access AWS
- Instead, Create an IAM user for yourself as well, give that user administrative permissions, and use that IAM user for all your work
- Disable Access Keys for Root User
  
- [**AWS tasks that require Root User Credentials**](https://docs.aws.amazon.com/general/latest/gr/aws_tasks-that-require-root.html)

#### [Password Policy](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_account-policy.html)

#### [Multi-Factor Authentication](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa.html)

<!-- Sub-Section Demarkation -->
### [Groups](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups.html)

- An IAM group is a collection of IAM users
- Groups let you specify permissions for multiple users

### [Roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html)

- An IAM identity that you can create in your account that has specific permissions
- Instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it
- Also, a role does not have standard long-term credentials such as a password or access keys associated with it
- When you assume a role, it provides you with *temporary security credentials* for your role session
- Use roles to delegate access to users, applications, or services that don't normally have access to your AWS resources

- [**Prefer Roles**](https://docs.aws.amazon.com/general/latest/gr/aws-access-keys-best-practices.html#use-roles)
  
- [**Identity Providers and Federation**](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers.html)


#### [Temporary Security Credentials](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp.html)

## [Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html)

- A policy is an object in AWS that, when associated with an identity or resource, defines their permissions
- AWS evaluates these policies when a principal entity (*user or role*) makes a request
- Permissions in the policies determine whether the request is allowed or denied
- Most policies are stored in AWS as **JSON** documents
- 6 types of policies:
  - **Identity-based policies**
    - Attached to an IAM Identity (user, group or role)
    - Could be *managed* or *inline* polices
  - **Resource-based policies**
    - Attached to resource (S3 bucket)
    - Always *inline*
  - Permissions Boundaries
  - Organizations SCPs
  - Access Control Lists
  - Session Policies

### [Managed and Inline Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html)

### [Identity vs Resource Based Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_identity-vs-resource.html)

### [Roles vs Resource based policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_compare-resource-policies.html)

### [Policy Evaluation Logic](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_evaluation-logic.html)

## [IAM Best Practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)

- Grant Least Privilege
- Configure a Strong Password Policy for Your Users
- Enable MFA
- Use Roles for Applications That Run on Amazon EC2 Instances
- Use Roles to Delegate Permissions
- Do Not Share Access Keys
- Rotate Credentials Regularly
- Remove Unnecessary Credentials

