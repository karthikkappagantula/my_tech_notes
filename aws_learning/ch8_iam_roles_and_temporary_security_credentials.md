# IAM Roles and Temporary Security Credentials

## IAM roles
* Role is not a user that you login to
* Does not have long term access credentials
* Designed to be assumed by anyone who needs to make use of their of permissions
* You grant permissions to AWS resources via roles. This is similar to service accounts.

Everytime a role is assumed, IAM provides temporary security credentials that allow/deny the permissions based on the role policy.

## Cross-Account Access: Resource Permissions vs. Cross-Account Roles
There are 3 ways to provide access to your S3 buckets from external AWS accounts.
* IAM Roles
* Bucket Policies
* Bucket ACLs (Access Control Lists) 

It is recommended to use IAM cross-account roles as a general practice.




