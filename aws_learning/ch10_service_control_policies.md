# Service Control Policies
Service control policies when applied directly or indirectly to AWS accounts define what actions can be performed on what services within that account.
These policies do not actually grant the permissions. They only restrict what you can do if you have permissions. Usually can be used to whitelist or blacklist services.

If multiple SCPs apply to an account, only the overlap of those SCPs is permitted.


* JSON doc that can be directly applied to a AWS account/OU.
* Inherits downwards.
* SCPs have no effect on master account.
* Avoid using master accounts for any AWS services. Use it only for billing and user store. You cannot place any restrictions on the resources using service control policy.


* * *
Footer
* * *
[Previous](ch9_aws_accounts_and_aws_organizations.md)
[Next](ch11_aws_account_limits.md)
