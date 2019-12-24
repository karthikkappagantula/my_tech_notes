# Identity and Acess Management(IAM) Overview

Allows to control access to AWS services and resources. It manages identities and allows permissions to those entities. As a global service the pool of identities is shared accross all regions.

IAM service objectivies :
* Authentication -> who can access AWS resources/services.
* Autherization -> what actions can be performed on a AWS resource/service by an authenticated user.

IAM Manages followint through AWS CLI, AWS SDK, or AWS management console :
* Users   / individual users with login credentials 
* Groups  / individuals can be grouped together to make the access management easier by setting group level permissions.
* Roles   / users, applications and services may assume IAM roles, and IAM policy will determine the permissions of the user that assumed the role. For a IAM User permissions obtained through IAM role will preceed the permissions obtained through individual IAM policy setup for the user.
* IMA policies  / JSON documents to describe permissions with in AWS.
* Authentication attributes - Usernames, passwords, Access keys, Multi-factor authentications and Password policies.


If you wanted to interact with AWS services/resources -  (both are longterm access credentials. Usually do not expire)
 * For UI based, use Username and Password
 * For command line/API, use Access Keys

IAM users are granted access through IAM polices assigned to the user or group or roles. 
Users are real user identities, where as groups are organizational grouping to define polices permissions to all users in a group.
(You cannot login using group)

By default, any new IAM user you create in AWS account has no permission policies attached. If an IAM user is not given access to a service/resource it implies a "Implicit Deny"
If there is any explicit Deny, it always override a ALLOW permission.

A root user account by default has all permissions on AWS, but it is highly recommended to use roor user only to setup the first IAM user account with admin access through a IAM policy.
