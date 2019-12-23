# Identity and Acess Management(IAM) Overview

Allows to control access to AWS services and resources. It manages identities and allows permissions to those entities. As a global service the pool of identities is shared accross all regions.

Manages :
* Users
* Groups
* Roles
* IMA policies
* Authentication attributes - Usernames, passwords, Access keys, Multi-factor authentications and Password policies.

If you wanted to interact with AWS services/resources -  (both are longterm access credentials. Usually do not expire)
 * For UI based, use Username and Password
 * For command line/API, use Access Keys

IAM users are granted access through IAM polices assigned to the user or group or roles. 
Users are real user identities, where as groups are organizational grouping to define polices permissions to all users in a group.
(You cannot login using group)

By default, any new IAM user you create in AWS account has no permission policies attached. If an IAM user is not given access to a service/resource it implies a "Implicit Deny"
If there is any explicit Deny, it always override a ALLOW permission.

