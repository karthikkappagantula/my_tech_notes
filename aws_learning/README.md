# Table of contents <br /><a name="toc"></a>
1. [AWS Essentials](#aws_essentials)<br />
    * [Accounts](#aws_accounts)<br />
    * [Regions](#aws_regions)<br />
    * [Availability Zones](#aws_azs)<br />
    * [Edge Infrastructure](#aws_edge)<br />
    * [HA, FT, DR](#aws_ha_ft_dr)<br />
    * [Use cases](#aws_ha_ft_dr_usecase)<br />
    * [Disaster Recovery](#aws_dr)<br />
    * [Data Persistence](#aws_data_persistence)<br />
    * [OSI 7-layer Networking Model](#aws_osi_model)<br />
* * *
[Top](#toc)
* * *
2. [Accounts](#aws_accounts)<br />
    * [IAM Overview](#aws_iam)<br />
    * [IAM Identity and Resource Policies](#aws_iam_policies)<br />
    * [IAM Roles and Temporary Security Credentials](#aws_iam_roles)<br />
    * [AWS accounts and Organizations](#aws_org)<br />
    * [Service Control Policies](#aws_scp)<br />
    * [AWS Account Limits](#aws_acc_limits)<br />
    * [AWS Support Tiers](#aws_supp_tiers)<br />
    * [AWS Config](#aws_config)<br />
    * [AWS Service Catalog](#aws_service_catalog)<br />
    * [Resource Billing Modes: On-Demand, Reserved, and Spot](#aws_billing)<br />
    * [Identity Federation](#aws_id_fed) <br />
    * [IAM Permissions Boundaries](#aws_iam_permissions) <br />
    * [Policy Evaluation Logic](#aws_policy_eval) <br />
* * *
[Top](#toc)
* * *

# AWS Essentials <a name="aws_essentials"></a>

## AWS Accounts <a name="aws_accounts"></a>
Provides - Isolated domains (limited blast radius for any exploits. i.e., impacts only specific account)
  * Authentication - Authenticates users using that domain.
  * Authorization - Permissions to users to resources.
  * Billing - Single bill for the account.

Account Root User/Principle - Only this user will have access to above domains and can further authenticate/authorize other users. 
Root user have full unrestricted permissions to the account, and can create other IAM users with Zero permissions by default.

AWS IAM will provide the identity store and a permission store used during authentication and authorization stages.

* * *
[Top](#top)
* * * 
## Regions / macro scale isolation <a name="aws_regions"></a>
There are many global regions. Usually > 100s of KM apart. 
Example - us-east-1, eu-central-1 etc

## Availability Zones / Fault isolation domains <a name="aws_azs"></a>
Each region has multiple AZs. AZ names follow similar format as regions, but end with a letter.
Example - us-east-1a, us-east-1b, us-east-1c, us-east-1d etc.

Each AZ is usually one or more physical datacenters with the region. 
They are far enough that they are not impacted by local events. They are close enough to support high performance networking between these AZs, and fault isolation.

## Edge Infrastructure <a name="aws_edge"></a>
Smaller pockets of infrastructure distributed globally accross major cities. AWS selects major data centers in those major urban areas and put in an edge location.
Usually contains storage and content distribution functionality. This also provides edge based compute capability that usually allow with certain services such as CloudFront, abillity to distribute or cache content at the edge to improve user experience
Cannot be used to deploy a EC2/RDS instances. 

### Usual practices
* For high performance and fault isolation, usually AZs can used.
* For global high availability. Example - Netflix. Usually costs high.
* * *
[Top](#top)
* * * 

## Differences between High availability, Fault Tolerance, and Disaster Recovery <a name="aws_ha_ft_dr"></a>
* High availability: It is not ability to remove failure, but rather the ability to recover from it. Minimise availability issues/Quickly recover from a failure.
* Fault Tolerance: Have multiple redundancy so that a major failure can be effectively handled by another instance. This is becomes important in failures that are not easily recoverable (due a natural disaster). This usually is very expensive due to various technologies required for the orchestration.
* Disaster Recovery: Solely concerned with protecting the critical system data so that you can use that to recreate a working system. This is designed to occur when none of the processes work. Must be always planned for irrespective of the system being designed.

### Use cases <a name="aws_ha_ft_dr_usecase"></a>
* If you are asked to implement a high available and you actually implement fault tolerant system, it will cost the business more that it needs to.
* If you are asked to implement a fault tolerant system and you actually implement a highly available system it could actually put people's careers/lives at risk.

##### Examples:
* a boy riding a motorbike - No High Availability, No Fault Tolerant, No Disaster Recovery.

A boy cannot ride a motorbike if there any failure with motorbike engine or any accidental death of the rider.

* a family riding a car - High Availability, No Fault Tolerant, No Disaster Recovery.

With spare tyres available the family can continue their journey with a minor failure/downtime to fix the tyre. If the engine fails, the journey stops there.

* An aeroplace with more than one engine - High Availability, Fault Tolerant, No Disaster Recovery.

Any failure with one of the engine can be recovered easily due to availability of other engines. This makes the recovery from failure possible and fault tolerant.

* Air force pilot in a aircraft that has serious failure - High Availability, Fault Tolerant, Disaster Recovery.

Here Air force pilot is an important asset that can be protected by ejecting out of the failing plane.
* * * 
[Top](#top)
* * * 
## Disaster Recovery <a name="aws_dr"></a>
It is all about how to be build systems highly available, fault tolerance, provide good performance and also can recover in the event of a disaster.

* Recovery Point Objective (RPO)
The time between when a disaster occurs and the last recoverable copy of key business data  was created. 

This represents the amount of data you would loose. Minimize the length of this time period through regular backups, snapshots, and transaction logs) to avoid business disruptive data loss.

* Recovery Time Objective (RTO)
The time between when a disaster occurs and when the system can be restored to an operational state and handed over to the business for testing.

Improve this by decreasing the restore time through having spares tested, and ready to use, and enforcing efficient processes.

It is important to understand how each AWS service/product supports RPO/RTO.
* * *
[Top](#top)
* * * 
## Data Persistence <a name="aws_data_persistence"></a>

Picking a correct type of storage is both important from a risk perspective and performance perspective.

### Types of Storage -
* Ephemeral Storage: 
Data that is generally local to a resource and is lost when that resource is powered down/fails.
Each EC2 instance is attached to a physical machines that usually that have attached storage. This data access is fast(instant store volumes) = less through-put.
Limitation - data loss when a machine failure/EC2 instance failure.
Example: Cache storage(Amazon ElastiCache).

* Persistent Storage:
Data that is durable and survives power events (Start, Stop, Restart).
Data access performance is not as fast as for Ephemeral Storage, but the data integrity is maintained.
Example: Amazon EBS, Amazon EFS

* Transient Storage:
Data that exists in a form while it is passed between sources. This helps in decoupling the application systems.
Example: Amazon Simple Queue Service (SQS)

* * * 
[Top](#top)
* * * 
## OSI Model <a name="aws_osi_model"></a>

[Wiki](https://en.wikipedia.org/wiki/OSI_model) for 7 layer OSI model.

Understanding of OSI model is essential to understand how any internet/networking application works.
This model is comprised of 7 layers.

No | Layer | Protocol data unit (PDU) | Function
---|-------| -------------------------|---------
 7 | Application  | Data | High-level APIs, including resource sharing, remote file access
 6 | Presentation | Data | Translation of data between a networking service and an application; including character encoding, data compression and encryption/decryption
 5 | Session | Data | Managing communication sessions, i.e., continuous exchange of information in the form of multiple back-and-forth transmissions between two nodes
 4 | Transport | Segment, Datagram | Reliable transmission of data segments between points on a network, including segmentation, acknowledgement and multiplexing
 3 | Network | Packet | Structuring and managing a multi-node network, including addressing, routing and traffic control
 2 | Data link | Frame | Reliable transmission of data frames between two nodes connected by a physical layer
 1 | Physical | Symbol | Transmission and reception of raw bit streams over a physical medium

* * * 
[Top](#top)
* * * 
# Accounts <a name="aws_accounts"></a>
## Identity and Acess Management(IAM) Overview <a name="aws_iam"></a>

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
* * *
[Top](#top)
* * * 
## Identity and Resource Policies <a name="aws_iam_policies"></a>
### Identity policy
An IAM policy is basically a JSON file consisting statements. Usually a statement consisting of 3 key-value pairs.
* Effect - Determines whether the access is allowed or denied
* Action - List of APIs calls on AWS resource. Can have Single or List of actions or All (done using `*`) or mix of both (`S3:*`)
* Resource - Which resource the statement applies to.
* Condition - adds conditional permissions.

Simple example of a statement allowing all actions on S3 on any AWS resource:
```
{ 
  "Version" : "2019-01-01",
  "Statement" : {
      {
        "Effect" : "Allow",
        "Action" : "s3:*",
        "Resource" : "*"
      }
   }
}
```

It is always best to use AWS managemened identity policies or custom identity policies rather than using policy for each user.

### Resource policy
An IAM policy that applies to particular AWS resource. A deny policy on a resource will override any allow identity policy.
Principal is required/mandatory for a resource policy which is the identity trying to access resource. Identity can be a non IAM user too, like a user trying to access a image from bucket through publicly hosted website through resource policy set to allow access.

#### Important points:
* An explicit deny will override any explicit allow permissions.

#### AWS official documents
IAM Policy ->  https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies.html
* * * 
[Top](#top)
* * * 
## IAM Roles and Temporary Security Credentials <a name="aws_iam_roles"></a>
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
* * * 
[Top](#top)
* * * 
## AWS Accounts and AWS Organizations
### AWS Organization <a name="aws_org"></a>
* Is a service that lets you consolidate multiple AWS accounts in to a single organization - a master account/root container.
* This makes billing and permissions easier and allows for the creation of managed accounts. 
* Can be further split in to Organization units(OU) which contains accounts - like one OU for each business unit.
* Can be operated in either 'Consolidated Billing' or 'All Features' mode.
* * * 
### Service Control Policies <a name="aws_scp"></a>
Service control policies when applied directly or indirectly to AWS accounts define what actions can be performed on what services within that account.
These policies do not actually grant the permissions. They only restrict what you can do if you have permissions. Usually can be used to whitelist or blacklist services.

If multiple SCPs apply to an account, only the overlap of those SCPs is permitted.


* JSON doc that can be directly applied to a AWS account/OU.
* Inherits downwards.
* SCPs have no effect on master account.
* Avoid using master accounts for any AWS services. Use it only for billing and user store. You cannot place any restrictions on the resources using service control policy.

* * *
[Top](#top)
* * * 
### AWS Account Limits/Service Quotas <a name="aws_acc_limits"></a>
This details the cut-off limits that AWS service supports. Most of these are hard cut-offs that play a crucial role in determining system design.

#### AWS Documentation
AWS Service Quotas -> https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html <br />
IAM and STS limits -> https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-limits.html

* * *
[Top](#top)
* * * 
### AWS Support Tiers <a name="aws_supp_tiers"></a>
There are 3 support plans apart from Basic free tien plan.
* Developer
   1. POCs/Experiments & Explore solutions
   2. Business hours email access to support engineers. Unlimited cases and 1 primary contact.
   3. General Architectural guidane.
   
* Business
   1. Production workloads for medium scale applications
   2. 24 X 7 phone, email and chat access to support engineers. Unlimited cases and contacts.
   3. Contextual Architectural guidane to use-cases
   
* Enterprise
   1. Large scale mission critical Production workloads.
   2. 24 X 7 phone, email and chat access to support engineers. Unlimited cases and contacts. 
   3. Consultative review and guidance based on your application.
   4. Access to Dedicated technical manager.
   
#### AWS Documentation
https://aws.amazon.com/premiumsupport/plans/
* * * 
[Top](#top)
* * * 
### AWS Config <a name="aws_config"></a>
AWS configuration management system - a managed AWS service that gives detailed view of the configuration of AWS resources(EC2, EBS, VPC etc.

Provides - 
* Ability to monitor all the AWS resources of a account over time.
* Ability to check for compliance of AWS resources for standards/rules.
* Ability to check the relationship between AWS resources.

Key Components - 
* Configuration recorder - Tracks every change made to AWS resource in an AWS account. Enabled per region basis. Needs an IAM role to provide necessary permissions for recorder to perform its functionality.

Key Terms - 
* AWS resource - Any resource that can be configured and tracked in a AWS account. S3 bucker, EC2, RDS, VPC, etc.
* Configuration Item(CI) - Record/State of a particular AWS resource at a point in time. 
* Configuration History(CH) - Collection of CIs at a time going backward in time for a AWS resource. One can know what changes were made to a resource since the establishment.
* * * 
[Top](#top)
* * * 
### AWS Service Catalog <a name="aws_service_catalog"></a>
Provides the abilit to implements IT Service Catalog in AWS. Usually used for larger organizations that have formal IT processes.

Service Catalog is a product which allows administrators to define products and portfolios(groups of products and configuration). Users can be allowed to self-service deploy these products without the usual IAM permissions required to do so directly with AWS services. 

CloudFormation Template is used to create portfolio/products along with permission details that will be used to provide self-service ability to product/service.

#### AWS documentation
https://docs.aws.amazon.com/servicecatalog/latest/adminguide/getstarted-iamenduser.html
* * * 
[Top](#top)
* * * 
### Resource Billing Modes: On-Demand, Reserved, and Spot<a name="aws_billing"></a>
AWS provides three billing models.
   * On-demand
      1) Default AWS billing Model. 
      2) Ideally suites an adhoc usage for POCs/experiments. 
      3) No discounts.
      4) Pay for what you consume. $ per hour, $ per GB transferred.
      5) Standard Startup priority - mostly used for shortterm usage.
   
   * Reserved
      1) Billing based on committed usage for 12 or 36 month term. You can pay "All upfront"/"Partial upfront"/"No Upfront" - with full upfront providing best cost advantage.
      2) Reservations can be used for EC2 instance, RDS instance, Dynamo DB performance and many other services in AWS.
      3) Reserved terms are useful when your usage is known and steady-state. This model can also reserve capacity.
      4) Provides high priority startup.

   * Spot
      1) Ideally suits for sporadic workloads - when you can tolerate interruptions and want the lowest price.
      2) Can be significantly cheaper than on-demand.
      3) Workloads need to be tolerant of interruptions, and resources can be terminated with very little notice.
      4) Lowest startup priority vs On-demand and Reserved.
  
AWS documentation -
https://aws.amazon.com/blogs/compute/new-amazon-ec2-spot-pricing/ <br />

See the following for the most updated information:
https://aws.amazon.com/ec2/pricing/ <br />
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-spot-instances.html <br />
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-capacity-reservations.html <br />
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-reserved-instances.html <br />
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-purchasing-options.html <br />
https://github.com/open-guides/og-aws#billing-and-cost-management <br />
* * * 
[Top](#top)
* * * 
### Identity Federation <a name="aws_id_fed"></a>
IAM roles + Security Token Services

Bridges two security domains (Like using AWS with Active directory).
* * * 
[Top](#top)
* * * 
### IAM Permissions Boundaries <a name="aws_iam_permissions"></a>
* * * 
[Top](#top)
* * * 
### Policy Evaluation Logic <a name="aws_policy_eval"></a>
* * * 
[Top](#top)
* * * 
