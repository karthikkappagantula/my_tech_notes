# Table of contents
1. [AWS Essentials](#aws_essentials)
    a. [Accounts](#aws_accounts)
    b. [Regions](#aws_regions)
    c. [Availability Zones](#aws_azs)
    d. [Edge Infrastructure](#aws_edge)
    e. [HA, FT, DR](#aws_ha_ft_dr)
        e1. [Use cases](#aws_ha_ft_dr_usecase)
    f. [Disaster Recovery](#aws_dr)
    g. [Data Persistence](#aws_data_persistence)
    h. [OSI 7-layer Networking Model](#aws_osi_model)
2. [Accounts](#aws_accounts)
    a. [IAM Overview](#aws_iam)
    b. [IAM Identity and Resource Policies](#aws_iam_policies)
    c. [IAM Roles and Temporary Security Credentials](#aws_iam_roles)
    d. [AWS accounts and Organizations](#aws_org)
    e. [Service Control Policies](#aws_scp)
    f. [AWS Account Limits](#aws_acc_limits)

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

### Differences between High availability, Fault Tolerance, and Disaster Recovery <a name="aws_ha_ft_dr"></a>
* High availability: It is not ability to remove failure, but rather the ability to recover from it. Minimise availability issues/Quickly recover from a failure.
* Fault Tolerance: Have multiple redundancy so that a major failure can be effectively handled by another instance. This is becomes important in failures that are not easily recoverable (due a natural disaster). This usually is very expensive due to various technologies required for the orchestration.
* Disaster Recovery: Solely concerned with protecting the critical system data so that you can use that to recreate a working system. This is designed to occur when none of the processes work. Must be always planned for irrespective of the system being designed.

#### Use cases <a name="aws_ha_ft_dr_usecase"></a>
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

* * *
#### AWS official documents
IAM Policy ->  https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies.html
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
### AWS Account Limits/Service Quotas <a name="aws_acc_limits"></a>
This details the cut-off limits that AWS service supports. Most of these are hard cut-offs that play a crucial role in determining system design.

* * * 
#### AWS Documentation
AWS Service Quotas -> https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html <br />
IAM and STS limits -> https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-limits.html

* * *

