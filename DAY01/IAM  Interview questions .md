1. What is IAM in AWS?
   Answer:
IAM (Identity and Access Management) is a web service that helps you securely control access to AWS services and resources. It allows you to create and manage users, groups, roles, and permissions.

3. What are the key components of IAM?
Answer:
Users – Individual AWS accounts.
Groups – Collection of IAM users.
Roles – Temporary permissions for users or services.
Policies – JSON documents that define permissions.

3.Identity providers (IdPs) – Used for federated access (e.g., SAML, OIDC).
| Feature     | IAM User                         | IAM Role                                    |
| ----------- | -------------------------------- | ------------------------------------------- |
| Identity    | Permanent                        | Temporary                                   |
| Use case    | Human user                       | EC2, Lambda, Federated users                |
| Credentials | Username/Password or Access Keys | No credentials; assumed by trusted entities |

4. What are IAM Policies?
Answer:
IAM Policies are JSON documents used to define permissions. They are attached to users, groups, or roles and define what actions are allowed or denied on specific resources.

5. What are the types of IAM policies?
Answer:
Managed policies – AWS or customer managed.
Inline policies – Embedded directly into a user, group, or role.
Permission boundaries – Limit maximum permissions a policy can grant.

6.6. What is a policy document structure?
Answer:
IAM policies use JSON with key elements:
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow" or "Deny",
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::example-bucket"
    }
  ]
}
7. What is the principle of least privilege?
Answer:
The principle of least privilege means giving users or services only the permissions necessary to perform their required tasks—nothing more
8. What is an IAM Role and when do you use it?
Answer:
IAM Role is an identity with no long-term credentials, used to grant permissions to:
AWS services (e.g., EC2 accessing S3)
Cross-account access
Federated users
9. How can you provide temporary access to IAM users?
Answer:
Use IAM roles with STS (Security Token Service) to generate temporary credentials.

10. What is AWS STS?
Answer:
AWS Security Token Service issues temporary credentials for IAM roles, users, or federated users to access AWS resources securely.
11. How to secure IAM best practices?
Answer:
Enable MFA for root and users.
Use roles for applications instead of hardcoded credentials.
Apply least privilege access.
Rotate access keys regularly.
Monitor activity with CloudTrail.
121. What is a trust policy in IAM?
Answer:
A trust policy defines who can assume a role. It's different from a permission policy which defines what actions are allowed.
13. What is the IAM policy simulator?
Answer:
IAM Policy Simulator is an AWS tool to test and troubleshoot IAM and resource policies to see if they grant the expected permissions.
14. How do you manage access to S3 buckets using IAM?
Answer:
Attach IAM user/role policies for access.
Use bucket policies for fine-grained permissions.
Enable ACLs (less preferred).
Use S3 Access Points for complex scenarios.

15. Real-Time Scenario: How do you allow an EC2 instance to access S3?
Answer:
Create an IAM role with S3 permissions.
Attach the role to the EC2 instance.
Application on EC2 uses the role automatically (via Instance Metadata Service) to access S3.
16. What happens if a user has both an Allow and Deny policy?
Answer:
Explicit Deny always overrides Allow. IAM evaluates policies with the most restrictive rule taking precedence.
17. How do you implement cross-account access in IAM?
Answer:
Create an IAM Role in Account A with trust policy allowing Account B to assume it.
In Account B, the user assumes the role via AWS CLI or SDK.
18. Can an IAM role assume another role?
Answer:
Yes, via chained role assumption, but it requires proper trust relationships and permissions.

19. What is the difference between IAM Policy and Resource Policy?
Feature	IAM Policy	Resource Policy
Attached to	IAM entities (user/role/group)	AWS resources (like S3 buckets)
Example	Role to allow S3 access	Bucket policy allowing specific user access

20. Can a single IAM user belong to multiple groups?
Answer:
Yes, and the union of all group policies applies to the user.

✅ Real-Time Challenges Faced in IAM
Challenge	Description
Over-permissioning	Users granted more access than needed. Fixed by using least privilege.
Credential leakage	IAM user access keys leaked in code/repos. Fixed by rotating and using roles.
Troubleshooting access issues	Difficult without using IAM Policy Simulator or CloudTrail logs.
Cross-account permission issues	Misconfigured trust/permission policies in cross-account roles.











