# IAM Roles and Temporary Security Credentials

## IAM roles
* Role is not a user that you login to
* Does not have long term access credentials
* Designed to be assumed by anyone who needs to make use of their of permissions
* You grant permissions to AWS resources via roles. This is similar to service accounts.

Everytime a role is assumed, IAM provides temporary security credentials that allow/deny the permissions based on the role policy.

