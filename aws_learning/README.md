##### Linux Academy Presentation - https://interactive.linuxacademy.com/diagrams/OrionPapersPro.html <br />

# Table of Contents
- [Table of Contents](#table-of-contents)
- [AWS Essentials](#aws-essentials)
  - [AWS Accounts](#aws-accounts)
  - [Regions / macro scale isolation](#regions--macro-scale-isolation)
  - [Availability Zones / Fault isolation domains](#availability-zones--fault-isolation-domains)
  - [Edge Infrastructure](#edge-infrastructure)
    - [Usual practices](#usual-practices)
  - [Differences between High availability, Fault Tolerance, and Disaster Recovery](#differences-between-high-availability-fault-tolerance-and-disaster-recovery)
    - [Use cases](#use-cases)
        - [Examples:](#examples)
  - [Disaster Recovery](#disaster-recovery)
  - [Data Persistence](#data-persistence)
    - [Types of Storage -](#types-of-storage--)
  - [OSI Model](#osi-model)
- [Accounts](#accounts)
  - [Identity and Acess Management(IAM) Overview](#identity-and-acess-managementiam-overview)
    - [IAM Security Token Service(STS)](#iam-security-token-servicests)
      - [When to use STS:](#when-to-use-sts)
  - [Identity and Resource Policies](#identity-and-resource-policies)
    - [Identity policy](#identity-policy)
    - [Resource policy](#resource-policy)
      - [Important points:](#important-points)
      - [AWS official documentation](#aws-official-documentation)
  - [IAM Roles and Temporary Security Credentials](#iam-roles-and-temporary-security-credentials)
  - [IAM roles](#iam-roles)
  - [Cross-Account Access: Resource Permissions vs. Cross-Account Roles](#cross-account-access-resource-permissions-vs-cross-account-roles)
  - [AWS Accounts and AWS Organizations](#aws-accounts-and-aws-organizations)
    - [AWS Organization](#aws-organization)
    - [Service Control Policies](#service-control-policies)
    - [AWS Account Limits/Service Quotas](#aws-account-limitsservice-quotas)
      - [AWS Documentation](#aws-documentation)
    - [AWS Support Tiers](#aws-support-tiers)
      - [AWS Documentation](#aws-documentation-1)
    - [AWS Config](#aws-config)
    - [AWS Service Catalog](#aws-service-catalog)
      - [AWS documentation](#aws-documentation-2)
    - [Resource Billing Modes: On-Demand, Reserved, and Spot](#resource-billing-modes-on-demand-reserved-and-spot)
    - [Identity Federation](#identity-federation)
    - [IAM Permissions Boundaries](#iam-permissions-boundaries)
    - [Policy Evaluation Logic](#policy-evaluation-logic)
  - [Networking in AWS: Virtual Private Clouds (VPCs)](#networking-in-aws-virtual-private-clouds-vpcs)
    - [VPC Basics](#vpc-basics)
      - [Connection between VPCs](#connection-between-vpcs)
      - [Useful links](#useful-links)
    - [AWS Resource Access Manager(RAM)](#aws-resource-access-managerram)
      - [AWS documentation](#aws-documentation-3)
    - [VPC Routing](#vpc-routing)
    - [Network Access Control Lists (NACLs)](#network-access-control-lists-nacls)
    - [Security Groups (SG)](#security-groups-sg)
    - [Public vs Private Subnets, Internet Gateways, and IP addressing](#public-vs-private-subnets-internet-gateways-and-ip-addressing)
    - [DNS in a VPC](#dns-in-a-vpc)
    - [VPC Flow Logs](#vpc-flow-logs)
    - [Using VPC Endpoints](#using-vpc-endpoints)
    - [Peering VPCs](#peering-vpcs)
      - [Limitations and Considerations](#limitations-and-considerations)
    - [AWS Site-to-Site VPN](#aws-site-to-site-vpn)
    - [AWS Direct Connect Architecture](#aws-direct-connect-architecture)
      - [AWS Direct Connect Architecture](#aws-direct-connect-architecture-1)
    - [AWS Transit Gateway](#aws-transit-gateway)
  - [Security](#security)
    - [Account and Service Security](#account-and-service-security)
      - [AWS Key Management(KMS)](#aws-key-managementkms)
      - [AWS CloudHSM](#aws-cloudhsm)
      - [AWS Certificate Management(ACM)](#aws-certificate-managementacm)
      - [AWS Directory Service](#aws-directory-service)
    - [Network Security](#network-security)
  - [EC2 Concepts](#ec2-concepts)
    - [Amazon Machine Image(AMI)](#amazon-machine-imageami)
    - [EC2 Instance types and Virtualization](#ec2-instance-types-and-virtualization)
    - [EC2 Storage Options](#ec2-storage-options)
      - [Elastic Block Storage (EBS)](#elastic-block-storage-ebs)
      - [Instance Storage Volumes - Ephemeral](#instance-storage-volumes---ephemeral)
    - [EC2 Instance Profiles and Roles](#ec2-instance-profiles-and-roles)
    - [Placement Groups](#placement-groups)
    - [Custom Logging to CloudWatch](#custom-logging-to-cloudwatch)
  - [Containers](#containers)
    - [Amazon Elastic Container Service (ECS)](#amazon-elastic-container-service-ecs)
      - [ECS Architecture](#ecs-architecture)
   

   
* * *
[Top](#table-of-contents-)
* * *
# AWS Essentials

## AWS Accounts
Provides - Isolated domains (limited blast radius for any exploits. i.e., impacts only specific account)
  * Authentication - Authenticates users using that domain.
  * Authorization - Permissions to users to resources.
  * Billing - Single bill for the account.

Account Root User/Principle - Only this user will have access to above domains and can further authenticate/authorize other users. 
Root user have full unrestricted permissions to the account, and can create other IAM users with Zero permissions by default.

AWS IAM will provide the identity store and a permission store used during authentication and authorization stages.

* * *
[Top](#table-of-contents-)
* * * 
## Regions / macro scale isolation
There are many global regions. Usually > 100s of KM apart. 
Example - us-east-1, eu-central-1 etc

## Availability Zones / Fault isolation domains
Each region has multiple AZs. AZ names follow similar format as regions, but end with a letter.
Example - us-east-1a, us-east-1b, us-east-1c, us-east-1d etc.

Each AZ is usually one or more physical datacenters with the region. 
They are far enough that they are not impacted by local events. They are close enough to support high performance networking between these AZs, and fault isolation.

## Edge Infrastructure
Smaller pockets of infrastructure distributed globally accross major cities. AWS selects major data centers in those major urban areas and put in an edge location.
Usually contains storage and content distribution functionality. This also provides edge based compute capability that usually allow with certain services such as CloudFront, abillity to distribute or cache content at the edge to improve user experience
Cannot be used to deploy a EC2/RDS instances. 

### Usual practices
* For high performance and fault isolation, usually AZs can used.
* For global high availability. Example - Netflix. Usually costs high.
* * *
[Top](#table-of-contents-)
* * * 

## Differences between High availability, Fault Tolerance, and Disaster Recovery
* High availability: It is not ability to remove failure, but rather the ability to recover from it. Minimise availability issues/Quickly recover from a failure.
* Fault Tolerance: Have multiple redundancy so that a major failure can be effectively handled by another instance. This is becomes important in failures that are not easily recoverable (due a natural disaster). This usually is very expensive due to various technologies required for the orchestration.
* Disaster Recovery: Solely concerned with protecting the critical system data so that you can use that to recreate a working system. This is designed to occur when none of the processes work. Must be always planned for irrespective of the system being designed.

### Use cases
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
[Top](#table-of-contents-)
* * * 
## Disaster Recovery
It is all about how to be build systems highly available, fault tolerance, provide good performance and also can recover in the event of a disaster.

* Recovery Point Objective (RPO)
The time between when a disaster occurs and the last recoverable copy of key business data  was created. 

This represents the amount of data you would loose. Minimize the length of this time period through regular backups, snapshots, and transaction logs) to avoid business disruptive data loss.

* Recovery Time Objective (RTO)
The time between when a disaster occurs and when the system can be restored to an operational state and handed over to the business for testing.

Improve this by decreasing the restore time through having spares tested, and ready to use, and enforcing efficient processes.

It is important to understand how each AWS service/product supports RPO/RTO.
* * *
[Top](#table-of-contents-)
* * * 
## Data Persistence

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
Example: Amazon Elastic Block Storage, Amazon Elastic File Storage

* Transient Storage:
Data that exists in a form while it is passed between sources. This helps in decoupling the application systems.
Example: Amazon Simple Queue Service (SQS)

* * * 
[Top](#table-of-contents-)
* * * 
## OSI Model

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
[Top](#table-of-contents-)
* * * 
# Accounts
## Identity and Acess Management(IAM) Overview

Allows to control access to AWS services and resources. It manages identities and allows permissions to those entities. As a global service the pool of identities is shared accross all regions.

IAM service objectivies :
* Authentication -> who can access AWS resources/services.
(Username/password for web and access keys for CLI/API access)
* Authorization -> what actions can be performed on a AWS resource/service by an authenticated user.

IAM Manages following through AWS CLI, AWS SDK, or AWS management console :
* Users   / individual users with login credentials 
* Groups  / individuals can be grouped together to make the access management easier by setting group level permissions.
* Roles   / users, applications and services may assume IAM roles, and IAM policy will determine the permissions of the user that assumed the role. For a IAM User permissions obtained through IAM role will preceed the permissions obtained through individual IAM policy setup for the user.
* IAM policies - JSON documents to describe permissions with in AWS.

IAM Policy Example: Below allows all S3 Operations
<pre>
{
  "Version": "2020-01-20",
  "Statement": [
    {
      "Effect" : "Allow",
      "Action" : "s3:*" ,
      "Resource" : "*"
    }
  ]
}

</pre>

IAM policy can set to Identities or Resources. 
* Identity policies - what a IAM user can access.
* Resource policies - what actions can be performed by any IAM user on the resource.

IAM Policies also allows you to use variables in the policy documents to create generic policy document.This is done using **Condition** key value pair.
*  comes in use to allow a IAM user to access only to the folder(folder name same as IAM user name) that he has permission to. 
*  Allow access to buckets only after certain time.

---------

Authentication attributes - Usernames, passwords, Access keys, Multi-factor authentications and Password policies.


If you wanted to interact with AWS services/resources -  (both are longterm access credentials. Usually do not expire)
 * For UI based, use Username and Password
 * For command line/API, use Access Keys

IAM users are granted access through IAM polices assigned to the user or group or roles. 
Users are real user identities, where as groups are organizational grouping to define polices permissions to all users in a group.
(You cannot login using group)

By default, any new IAM user you create in AWS account has no permission policies attached. If an IAM user is not given access to a service/resource it implies a "Implicit Deny"
If there is any explicit Deny, it always override other ALLOW permission.

A root user account by default has all permissions on AWS, but it is highly recommended to use roor user only to setup the first IAM user account with admin access through a IAM policy.

* * *
[Top](#table-of-contents-)
* * *
### IAM Security Token Service(STS)
* STS allows you to create temporary security credentials that grant trusted users access to your AWS resouces.
* Short-term credentials - configurable session duration between 15 minutes and 12 or 36 hours.
* STS API call returns a credential object with - 
   1. Session Token
   2. Access Key ID
   3. Secret Access Key
   4. Expiration Timestamp
 
#### When to use STS:
* Identity fedaration - authenticate through your company network.
* Supports Security Assertion Markup Language(SAML), which allows Microsoft Active directory.
* Web identity federation (Google, Amazon, Twitter etc)
* Roles for Cross-Account access - used for organizations that have more than one AWS account.
* Roles for Amazon EC2 and other services - granting access to application running on EC2 to other AWS service without having to imbed credentials.

*NOTE - For Mobile applications AWS recommends using Cognito rather than STS.*


* * *
[Top](#table-of-contents-)
* * * 
## Identity and Resource Policies

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

#### AWS official documentation
https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html
https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition.html
https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_variables.html

* * * 
[Top](#table-of-contents-)
* * * 
## IAM Roles and Temporary Security Credentials 

## IAM roles
* Role is not a user that you login to
* Does not have long term access credentials
* Designed to be assumed by anyone who needs to make use of their of permissions
* You grant permissions to AWS resources via roles. This is similar to service accounts.
* A role has two components - 
  * trust policy - defines circumstances under which role can be assumed
  * permission policy - defines AWS access rights granted during "AssumeRole"


Everytime a role is assumed, IAM provides temporary security credentials that allow/deny the permissions based on the role policy.

Curl on http://169.254.169.254/latest/meta-data/iam/security-credentials/*role-name*
will display the role credentials. (change *role-name* to role assumed)

Running an sts:Assume role API call results in STS providing you with temporary credentials.

You can either -
* remove the permission policy for the role to stop allowing access to AWS resource. Impacts all who assumes the role.
* revoke session. Impacts only unauthorized access.

**AWS Official Documentation**
https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2-instance-metadata.html

## Cross-Account Access: Resource Permissions vs. Cross-Account Roles
There are 3 ways to provide access to your S3 buckets from external AWS accounts.
* IAM Roles
* Bucket Policies
* Bucket ACLs (Access Control Lists) - legacy method attached to objects

**It is recommended to use IAM cross-account roles as a general practice**. Both ACLs and Bucket Policies will prevent bucket owner the access to the object created in the bucket by another user.

**AWS Official Documentation**

Granting Cross-Account Permissions Example - 
<https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html#example-bucket-policies-use-case-8>

IAM Policies and Bucket Policies and ACLs! Oh, My! (Controlling Access to S3 Resources) - 
https://aws.amazon.com/blogs/security/iam-policies-and-bucket-policies-and-acls-oh-my-controlling-access-to-s3-resources/
* * * 
[Top](#table-of-contents-)
* * * 
## AWS Accounts and AWS Organizations
### AWS Organization
* Is a service that lets you consolidate multiple AWS accounts in to a single organization - a master account/root container.
* This makes billing and permissions easier and allows for the creation of managed accounts. 
* Can be further split in to Organization units(OU) which contains accounts - like one OU for each business unit.
* Attaching policies at Root/OU levels will propagate to all accounts with in that Rote level/OU level respectively(inherit downwards through the heirarchy).
* Can be operated in either 'Consolidated Billing' or 'All Features' mode.
  * Consolidated billing - Single AWS usage bill with granular details. Helps to achieve usage discounts quicker and efficiently.

  
* * * 
### Service Control Policies
Service control policies when applied directly or indirectly to AWS accounts define what actions can be performed on what services within that account.
These policies do not actually grant the permissions. They only restrict what you can do if you have permissions. Usually can be used to whitelist or blacklist services.

If multiple SCPs apply to an account, only the overlap of those SCPs is permitted.


* JSON doc that can be directly applied to a AWS account/OU/Root container.
* Inherits downwards the hierarchy.
* SCPs have no effect on master account.
* SCPs contain explict ALLOW and DENY statements, but these statements don't GRANT Permisssions, they only say those permissions are permitted. They are kind of whitelisting/blacklisting actions that can be perfromed.
* Avoid using master accounts for any AWS services. Use it only for billing and user store. You cannot place any restrictions on the resources using service control policy or by any other means.
* If multiple SCPs apply to an account, only the overlap of those SCPs is permitted.

* * *
[Top](#table-of-contents-)
* * * 
### AWS Account Limits/Service Quotas
This details the cut-off limits that AWS service supports. Most of these are hard cut-offs that play a crucial role in determining system design.

#### AWS Documentation
AWS Service Quotas -> https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html <br />
IAM and STS limits -> https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-limits.html

* * *
[Top](#table-of-contents-)
* * * 
### AWS Support Tiers
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
[Top](#table-of-contents-)
* * * 
### AWS Config
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
[Top](#table-of-contents-)
* * * 
### AWS Service Catalog
Provides the ability to implements IT Service Catalog in AWS. Usually used for larger organizations that have formal IT processes.

Service Catalog is a product which allows administrators to define products and portfolios(groups of products and configuration). Users can be allowed to self-service deploy these products without the usual IAM permissions required to do so directly with AWS services. 

CloudFormation Template is used to create portfolio/products along with permission details that will be used to provide self-service ability to product/service.

#### AWS documentation
https://docs.aws.amazon.com/servicecatalog/latest/adminguide/getstarted-iamenduser.html
* * * 
[Top](#table-of-contents-)
* * * 
### Resource Billing Modes: On-Demand, Reserved, and Spot
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
[Top](#table-of-contents-)
* * * 
### Identity Federation
Identity fedaration bridges two security domains. AWS account is a separate security domain.

Internal AWS identity fedaration between master account and user account:
IAM roles + Security Token Services(STS). STS provides the temporary access tokens that lets you assume a IAM role - which is a kind of identity federation.

External AWS Identity fedaration:
Use a non AWS user id to login and use AWS resources. This is similar to using a in-house/active directory security domains ids for logging in to AWS. Like using your company email id as AWS login details.

Google, Facebook, Twitter are external identity providers(IDPs). They identify and authenticate the users. STS provides the temporary credetials that will be used for interacting with AWS resources/services.

Different Identity Federation
* AssumeRole - within AWS
* AssumeRoleWithWebIdentity - Integrated to Google/Twitter/Facebook etc.
* AssumeRoleWithSAML - Integrated to Active Directory.

IAM has a limit of 5000 user accounts. Identity federation solves this limitation.

Benefits - 
* administration of roles is easy and support any number of users.
* credentials are managed through sessions.

**AWS Official Documentation**
https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_saml.html https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_oidc_cognito.html
* * * 
[Top](#table-of-contents-)
* * * 
### IAM Permissions Boundaries

Permissions Boundaries limit the maximum permissions an identity can have. They can be applied to IAM Users/Roles/AWS organizations.

Permission Boundaries don't GIVE any permissions. they limit what permissions a thing can have. 

Given an IAM permissions policy and permission boundary - effective permissions are the intersections.(Works similar to Service Control Policy).

**AWS Official Documentation**
https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_boundaries.html

* * * 
[Top](#table-of-contents-)
* * * 
### Policy Evaluation Logic

Evaluation logic order ->

1. Organization Boundaries
2. User or Role Boundaries
3. Role Policies
4. Permissions

Boundaries are always processed first starting with organizational and then identity(user or role). Then AWS checks if you have chosen a subset of permissions for a stst:AssumeRole. Final effective permissions are a merge of identity, resource, and ACL.

**Evaluation Logic** <br>
Explicit DENY --> DENY <br>
Explicit ALLOW without Explicit DENY --> ALLOW <br>
No Explicit ALLOW/DENY --> DENY (Default)

**AWS Official Documentation**
https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_evaluation-logic.html

* * * 
[Top](#table-of-contents-)
* * * 

## Networking in AWS: Virtual Private Clouds (VPCs)
### VPC Basics
* Use VPC to create any private isolated networks domains.
VPC - foundational network elements in AWS.

Network Zones:
1. Private networks - accessible only to the owner/creator.
2. Public networks - accessible over on the internet.
3. AWS public zone - S3/Dynamo DB/Cloud watch logs can be accessed through end points from both private/public networks.

Each AWS account has a default VPC(only one) for the region of your account. Certain AWS services depend on this default VPC.
A VPC can be set to two tenancy modes:
* Default - shared hardware systems/resources
* Dedicated - dedicatedly hardware resources.

A VPC contains Subnets. Subnets occupy a AZ/subset of VPC CIDR range. A subnet is where your resources reside.
Subnets CIDR range occupy some portion of CIDR range of VPC.
Within every VPC subnet a number of IP addresses reserved:
(assuming 10.0.0.0/24 subnet)
   * 10.0.0.0 - network address
   * 10.0.0.1 - VPC router(network + 1)
   * 10.0.0.2 - DNS (network + 2)
   * 10.0.0.3 - Reserved for future use
   * 10.0.0.255 - Broadcast
 Primary DNS address in a VPC is VPC network + 2.

Cloud Formation templates can be used to create VPCs/Subnets.

<pre>
NOTE: 
Basic recommendation for No of subnets in AWS = No of AZs we want to deploy to X No of application tiers(UI/DB/etc).
This is not a hard rule and a new subnet should be created as required.
</pre>


#### Connection between VPCs
* VPC peers - connects individual VPCs to other VPCs in same/other region/zones.
* Internet gateways - connection over internet.
* VPN gateways - connection to On-premise resources.
* Bastion Host - 
* VPC end points
* Egress only Internet gateway

#### Useful links
[IP Subnetting the Easy Way](https://www.theprohack.com/2012/01/ip-subnetting-easy-way.html)
* * * 
[Top](#table-of-contents-)
* * * 
### AWS Resource Access Manager(RAM)
A service that allows the sharing of AWS resources between accounts (VPC owner vs VPC participant).

* Enable sharing within your organization in RAM before sharing any resources between accounts - handshake is not required.
* AZ id - AZ name is generic and they remain same for all users of AWS. AZ id is unique id that maps to a physical hardware, and is consistent for all accounts. AZ name can be different between Dev and Prod accounts.
* Resource share - By creating a resource share in AWS RAM  you share set of AWS resources within/outside organization. Sharing is limited based on the resources being shared. Subnets are not allowed to be shared outside of organization.

VPC owner - responsible for maintaining VPCs and its components(Subnets, Network ACLs,Peering Connections, Routing connections, End points, etc).

VPC participant - responsibility of only resources created by participants. All other shared resources are read-only.

While Resource manager allows to share resources to accounts from other organizations. But there are limits to what can be shared. Subnets can only be shared to other accounts with in same organization. Default resources(subnets/security policies) cannot be shared to any accounts.


#### AWS documentation
[Enabling RAM](https://console.aws.amazon.com/ram/home#Setting)

[Working with AZ IDs](https://docs.aws.amazon.com/ram/latest/userguide/working-with-az-ids.html)

[What Is AWS RAM?](https://docs.aws.amazon.com/ram/latest/userguide/what-is.html)

[VPC Sharing](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-sharing.html)
* * * 
[Top](#table-of-contents-)
* * * 
### VPC Routing
VPC Router - 
* Every VPC has a VPC router - default gateway for VPC
* Occupies on ip address on every single subnet in the VPC(network + 1 address).
* VPC router is controlled by route tables. VPCs come with a default 'MAIN' Route table. Custom Route Tables can be defined and attached to subnets(one route per subnet or collection of subnets using shared route table).
* Route tables contain a default 'local' route that cannot be changed/deleted.
* A route matches a destination and tells the VPC router where to direct IP traffic. More specific routes take priority(i.e /32 > /16).
* Routes added to Route table can be static routes or Route propagation configs.
* VPC routers are used for VPC endpoints, VPC peering connections, Egress only Internet gateway, Internet gateway, NAT-Gateway.

* * * 
[Top](#table-of-contents-)
* * * 
### Network Access Control Lists (NACLs)
NACLs are firewalls attached to VPC subnets. They filter IP traffic entering or leaving the subnet. NACLs are STATELESS which means ephemeral port rules are required to allow 'response' traffic.
* A subnet can have one associated NACLs acting as a barrier between VPC and its subnet.
* VPCs have a defailt NACLs associated with any subnets in that VPC by default that allows both inbound and outbound traffic.
* Inbound rules are applied for traffic coming in to subnets.
* Outbound rules are applied for traffic coming out of the subnets.
* Rules priority is done based on Rule # field. Lowest Rule # will take higher priority over a higher Rule # entry.
* Rules are based on IP address ranges only, and cannot refer any logical resources and are processed with lesser rule number taking higher priority.
* Common use case for NACLs - Whitelist/Blacklist traffic from/to an IP.
* NACLs does not effect traffic between two EC2 instances with in same Subnet. They come in to effect only when the traffic is flowing in to/out of a Subnet.
* NACLs are the only option when Security groups cannot be used to restrict the routing. 
* NACLs take effect only for traffic flowing in and out of a subnet. Traffic between resources in same subnet cannot be effected by NACLs.

[Wiki for Ephemeral port](https://en.wikipedia.org/wiki/Ephemeral_port)
* * * 
[Top](#table-of-contents-)
* * * 
  
### Security Groups (SG)

Security Groups are filtering products in AWS, applied only to networks resources inside VPC and effect the traffic coming in/to them.

* Every VPC comes with a default SG
* Each SG contains inbound/outbound rules for IP traffic.
* SG procesing has NO order - all rules are executed at once. There is a deafult implicit DENY. SG's cannot explicitly DENY.
* SG rules are STATEFUL. If traffic is allowed IN, it's corresponding return traffic is automatically allowed - this cannot be changed. The same applies to outbound traffic, its return communications are automatically permitted. ==> You do not have to worry about ephemeral ports.
* Can be used as role based security rules that can be used by any other security groups - reducing admin overhear.

* * * 
[Top](#table-of-contents-)
* * * 
  
### Public vs Private Subnets, Internet Gateways, and IP addressing

* A private subnet is a subnet with default configuration. It cannot communicate with public internet or AWS public zone networks(S3, DynamoDB etc).
* A public subnet requires the VPC to be able to connect to internet gateway (you have to create a internet gateway and attach to VPC) and should have custom route table with default traffic allowed for internet gateway.

*public IP for an instance can be inherited based on VPC config*

**Bastion Host** - An EC2 instance in a public subnet with public IP address, configured to accept connections from public internet. They are usually used for admin purpose to control/restric traffic from public internet to private resources.


[Connect to Amazon EC2 Using Putty Private Key on Windows](https://linuxacademy.com/blog/linux/connect-to-amazon-ec2-using-putty-private-key-on-windows/)

**NAT Gateways**
* NAT gateways provides NAT services - network address translation. 
* NAT gateway have single public IP. 
* When NAT Gateways receive any traffic from private instances, they convert the private IPs to the single Public IP and connects to Internet Gateway.
* NAT gateways are configured in Public Subnet and require Elastic IP addresse - static IP that does not change.
* Configurate NAT gateway in each AZ with in your account to support high availability.
* Use route tables to direct the traffic through NAT gateways.

**Internet Gateways** - allows INBOUND and OUTBOUND public internet and AWS Public Zone routing.

**Egress-Only Gateways** - allows OUTBOUND only public internet and AWS public Zone routing.
Egress-Only Gateways work similar to Internet Gateway, except that it is used for IPv6 addresses. IPv6 address are public routable addresses.

Senario - A resource has been allocated an IPv6 address, occupies a subnet with an applicated IPv6 CIDR which itself is part of a VPC with a IPv6 CIDR allocation.
Resources inside a public subnet with IPv6 allocations are provided with publically routable addresses - because all IPv6 addresses are publically routable.

NAT gateways are not a valid option to provide outgoing only access to the AWS public zone or public internet. Egress-Only Gateway is used to prevent any incoming traffic to such publicly routable IPv6 addresses.
Allocated VPC IPv6 + Allocated Subnet IPv6 + Allocated EC2 IPv6 + Egress-Only Gateway = Prevents public networks from accessing resources hosted on this VPC/Subnet/Instance.

[IPv6 Subnet Cheat Sheet and IPv6 Cheat Sheet Reference](https://www.crucial.com.au/blog/2011/04/15/ipv6-subnet-cheat-sheet-and-ipv6-cheat-sheet-reference/)<br>
[IPv6 Subnetting - Overview and Case Study](https://community.cisco.com/t5/networking-documents/ipv6-subnetting-overview-and-case-study/ta-p/3125702)<br>

* * * 
[Top](#table-of-contents-)
* * * 
  
### DNS in a VPC

* The Network+2(DNS server) reserved address is called R53 Resolver - and is accessible only with in a VPC.
* Thus DNS server is not accessible outside the VPC to any on premise servers through VPN connection or direct connection.
* One solution is to use EC2 instances as DNS relays that let the on-premise instances to talk to instances in VPC indirectly.
* Inbound/Outbound endpoints configuration in R53 resolver does the DNS resolving between VPC and on-prem/external/non-VPC networks.

[AWS documentation](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver.html)
* * * 
[Top](#table-of-contents-)
* * * 

### VPC Flow Logs

* Provides network traffic visibility (logging and monitoring toolset).
* Stores only Metadata, but not application data. Logged only -
  * versioning
  * account-id
  * interface-id
  * scraddr
  * dstaddr
  * srcport
  * dstport
  * protocol
  * packets
  * bytes
  * start
  * end
  * action
  * log-status
* **NOT LOGGED -** 
  * DHCP traffic
  * AWS DNS 
  * Internal AWS instances' Metadata 
  * License Activation Requests.
* Can setup monitoring logs for metadata at 3 different levels:
  * At VPC level (all traffic TO/FROM/INSIDE) the VPC.
  * At Subnet level(TO/FROM/INSIDE) the subnet.
  * At Elastic Network Interface(ENI) level(TO/FROM) the ENI.
* IAM Role is required for VPC flow log service - either for CloudWatch logs injection or to store log files in to an S3 bucket.

* * * 
[Top](#table-of-contents-)
* * * 
  
### Using VPC Endpoints
* VPC endpoints come in handy where you do not want any of you subnets/VPC instances to have access to public/internet networks.
* VPC endpoints allow services to be injected in to your VPC via a virtual devide in your VPC.
* VPC endpoints come in two types - Interface endpoints and Gateway endpoints - which you select will depend on the service you wish to allow.
* Endpoints can be utilised to allow access to AWS public zone services without giving resources public access.
* Endpoints can also be used to create 'private only' access to certain services such as S3 buckets.
* Gateway endpoints are logical Gateway entity that exists inside VPC rather than inside Subnet. They can be referenced in a route table.

* * * 
[Top](#table-of-contents-)
* * * 

### Peering VPCs

* VPC peering connections allow communication between isolated VPCs. They work fully-featured across accounts, and in a feature-limited way between AWS regions.
* VPC peering connections are created as logical objects - and require route table entries at both sides.
* CIDRs cannot overlap.
* Provides highly resilient and performance oriented easy solution to inter-connect VPCs.
* NACLs routes/SGs rules may need to be updated for routing restrictions that conflicts VPC peering connections. 
* Also have to ensure DNS resolution works correctly.

  
#### Limitations and Considerations

**Intra-region VPC Peering**
* Peering connections cannot peer VPC's with overlapping CIDRs
* Peering is not transitive. Peering A and B, B and C, does not mean A and C are peered.
* SGs can reference groups in remote VPC's. SGs and NACLs can also reference CIDR/IP.
* IPv6 is supported, but not by-default.
* Private DNS hostnames can be resolved.

**Inter-region VPC Peering**
* Inter(cross) Region peered VPCs do not support IPv6.
* Security group logical referencing does not work cross-region.
* Private DNS hostnames can be resolved but must be enabled.
  
* * * 
[Top](#table-of-contents-)
* * * 

### AWS Site-to-Site VPN 

* Product set allows to configure hardware based VPN connection between on-prem networks and VPCs.
* Provides fully encrypted communication channels.
* Contains 3 components:
  * Customer Gateway - physical hardware at on-prem side that allows static/dynamic routing.
  * Virtual Private Gateway - egree only gateway attached to a VPC.
  * VPN Connections - occurs between Customer gateways and Virtual Private Gateways.


* * * 
[Top](#table-of-contents-)
* * * 

### AWS Direct Connect Architecture 

#### AWS Direct Connect Architecture
* A service that provides a dedicated network connection between on-premise network and one of the AWS direct connect locations.
* Done through authorized Direct Connect Provider (e.g. ATT Netbond)
* An AWS direct connect location provides ability to access VPCs in the AWS region it is associated with.
* Access to public service endpoints in all regions.

**Benefits**
* Reduces network costs
  * Reduces bandwidth commitment to corporate ISP over public internet.
  * Data transfer cost is billed at a lower rate by Amazon.
* Increased network consistency
  * Dedicated private connections reduce latency
* Dedicated private network connection to on-premise
  * Connect direct connect connection to a VGW in your VPC for a dedicated private connection from on-premise to VPC.
  * Ability to bypass using bastion hosts for managing private resources.
  * Use multiple VIF(Virtual Interfaces) to connect to multiple VPCs.

**AWS documentation**

[Userguide](https://docs.aws.amazon.com/directconnect/latest/UserGuide/Welcome.html)

[Multiple Data Center HA Network Connectivity](https://aws.amazon.com/answers/networking/aws-multiple-data-center-ha-network-connectivity/)


* * * 
[Top](#table-of-contents-)
* * * 
  
### AWS Transit Gateway

* * * 
[Top](#table-of-contents-)
* * * 

## Security

### Account and Service Security

#### AWS Key Management(KMS)
* This is a part of IAM that manages Security keys for AWS.
* Provides role seperation.
* Generates and manages Customer Master Keys(CMK), using which KMS encrypt and decrypt small amounts of data up to 4kb.
* CMKs are logical representation of a key. CMKs can be generated or imported by KMS.
* KMS is a region specific service and CMKs never leave KMS and never leave a region.
* Access to CMK is only through KMS apis, and is controlled by Security roles.
* KMS uses CMK to access Data Encryption Key for encryption/decryption of the objects.
* Supports FIPS 140-2 - cryptographic specifications.

**AWS Documentation**
[Importing Keys](https://docs.aws.amazon.com/kms/latest/developerguide/importing-keys.html) <br>
[Envelope Encryptions](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#enveloping) <br>
[Protecting Encrypted Data Integrity](https://aws.amazon.com/blogs/security/how-to-protect-the-integrity-of-your-encrypted-data-by-using-aws-key-management-service-and-encryptioncontext/)<br>
[Grants](https://docs.aws.amazon.com/kms/latest/developerguide/grants.html)<br>
[Compliance](https://aws.amazon.com/kms/features/#compliance)


* * * 
[Top](#table-of-contents-)
* * * 

#### AWS CloudHSM

* Provides hardware security modules. KMS under the hood uses HSMs.
* CloudHSM is dedicated HSM which runs within your VPC, accessible only to you in a single tenant architecture.
* Runs within your VPC, accessible only to you in a single tenant architecture.
* Supports PKCS#11, Java Cryptography Extensions(JCE), Microsoft CryptoNG(CNG), while KMS does not support.
* Keys can be transferred between CloudHSM and other hardware solutions(on premises). Keys are shared between cluster members.
* Not High Avaiable unless multiple HSM's are provisioned.
* Supports FIPS 140-2 and FIPS 140-3 - cryptographic specifications.
* On-premises HSM - for if you really need to control your own physical hardware.

* * * 
[Top](#table-of-contents-)
* * * 

#### AWS Certificate Management(ACM)
* Manages X509 v3 SSL/TSL certificates.
* Certificates, containing public keys, are used in connecting to any https traffic that authorizes the access. (Private half of keys are held at web servers)
* ACM integrates with other AWS services and generates certificates that are valid for 13 months.
* No associated costs with Certificates - only the resources they are used with
* Certificates are automatically renewed when actively used within supported services.
* Native integration with ELB, CloudFront, AWS Elastic Beanstalk & API Gateway.
* Integrates with Route53 to perform DNS checks as part of certificate issuing process.
* ACM is regional - certificates can be applied to serviecs in that region.
* KMS is used - certificates are never stored unencrypted.

[AWS documentation](https://docs.aws.amazon.com/acm/latest/userguide/acm-concepts.html)

* * * 
[Top](#table-of-contents-)
* * * 

#### AWS Directory Service

* Group of products which include Amazon Cloud Directory, Microsoft(MS) Active Directory, Simple AD, AD connector and Amazon Cognito.
  
  | Directory Type | Features & Patterns | Anti-Patters |
  | :------------ |:-------------| :-----|
  | Simple AD | * Low cost basic directory service <br> * Integrates with AWS for SSO, and EC2/workspaces | * Cut-down version of MS AD directory. <br> * More complete enterprise apps won't work. <br> * Does not support TRUST relationships with MS AD |
  | MS Active Directory | * HA by design, running in multiple AZs | * Not suitable for large scale application. <br> * Expensive than Simple AD. <br> * Use only if MS based AD is required. |
  | AD Connector | * Proxy bridging between AWS Services and existing on-premise AD. <br> * Allows EC2 and Workspaces to integrate with on-premise AD | * In isolation provides NO authentication/authorization or directory services <br> * Requires an existing implementation |
  | Amazon Cognito | * Supports ID federation, user pool management, sign-on and more for web and mobile applications | * Not suited for traditional AD serviecs usage. <br> * Does not integrate with services in the same way |
  | Amazon Cloud Directory | * Graph based store of information. <br> * Manages object information, relationships, and schema management | * Not really suited to any workloads which manage 'users/groups' or 'identities' |

* * * 
[Top](#table-of-contents-)
* * * 

### Network Security


* * * 
[Top](#table-of-contents-)
* * * 

## EC2 Concepts

* Every EC2 instance is created using Amazon Machine Image(AMI).
* AMI 
  * images generally has root volume with OS installed.
  * usually comes with a vitualization technology built in.
* Different AMI types are available in marketplace, community or quick start(Amazon) menu options.
* A single EC2 occupies a single Subnet/VPC/Region/AZ.
  
### Amazon Machine Image(AMI)

* Amazon provided / maintained EC2 images.
* Each AMI contains (metadata) -
  * the information required to launch an instance
  * the owner of the AMI
  * launch permissions
  * system architecture (32 bit vs 64 bit processor)
  * operating systems
  * a block device mappings of all volumes(EBS volumn snapshots) required
* User can create their own AMI based on requirement.
* By default user who creates the AMI will have implicit ownership of the AMI allowing use by the creator.
* AMIs can be sold in marketplace as commercial instances with softwares. Users of these AMIs would pay standard EC2 charges and extra charges for the Image provider.
  
* * * 
[Top](#table-of-contents-)
* * * 
### EC2 Instance types and Virtualization

* All instances fall in to different families, grouped based on specific benefits when selected. Few examples - 
  * general purpose
  * memory optimized
  * storage optimized
  * cpu heavy
  
* **general purpose**
  * If no specific requirement, pick general purpose instance type.
  * M type is default type - not special in any way. 
    * if it ends with 'a' it using AMD processor
  * T type use if you know the operations to be under mentioned baselines for majority of times. For burstible requirements.
  * A type uses Arm architecture.

* **compute optimized**
  * for enhanced CPU capabilities.
  * C type. if it ends with 'n' it provides additional networking perfomance benefits.

* **memory optimized**
  * optiimized for memory consumption.
  * R type 
  * X type

* **storage optimized**
  * heavy storage usage / sustained disk throughput.
  * H type
  * I type
  * D type

* **accelerated computing**
  * high performance computing using GPUs for data analytics
  * P type - data analysis
  * G type - graphics
  * F type - genomics research, financial analytics, etc


**External Docs**

[EC2 Virtualization 2017](http://www.brendangregg.com/blog/2017-11-29/aws-ec2-virtualization-2017.html)

[Virtualization Technology](https://www.intel.com/content/www/us/en/virtualization/virtualization-technology/intel-virtualization-technology.html)

[EC2 Instance Types](https://aws.amazon.com/ec2/instance-types/)


* * * 
[Top](#table-of-contents-)
* * * 

### EC2 Storage Options

#### Elastic Block Storage (EBS)

* Network Storage Product.
* EBS optimised instances provide dedicated storate network - improving speeds and reducing contention with traditional data transfer.
* Volumes occupy an Availability Zone.
* Provides both SSD based volumes and HDD based volumes
  * general purpose (gp2) : SSD
    * default for most workloads
    * baseline performance of 3 IOPS/GiB - (100 IOPS - 16,000 IOPS p/vol)
    * bursts up to 3000 IOPS (credit based)
    * volume size of 1 GiB to 16 TiB
    * max throughput p/vol of 250 MiB
  * provisioned IOPS SSD (io1) : SSD
    * used for mission critical applications that require sustained IOPS performance
    * large database workloads
    * volume size of 4 GiB to 16 TiB
    * performs at provisioned level and can provision up to 64,000 IOPS p/volume
    * max throughput p/vol of 1000 MiB/s
  * throughput optimized(st1) : HDD
    * low storage cost
    * used for frequently accessed, throughput-intensive workloads (Streaming, Big data)
    * cannot be a boot volume
    * volume size of 500 GiB - 16 TiB
    * p/volume max throughput of 500 MiB/s & IOPS 500
  * code HDD (sc1) : HDD
    * lowest cost
    * infrequently accessed data
    * cannot be a boot volume
    * volume size of 500 GiB to 16 TiB
    * p/vol max throughput of 250 MiB/s & 250 IOPS
* Ideal patterns -
  * Persistence storage.
  * Durabitlity - allows for snapshots or resilience.
  * Elasticity - Scales based on demand.
  * Provisioned Performance - certain EBS volumes can provide guaranteed performance levels.
* Anti-patterns -
  * Temporary storage - EC2 instance store is better suited for it. EBS has costs attached and is best as persistent store.
  * Static conent distribution - S3 or S3+Cloudfront are ideal for it.
  * Shared access - EBS volumes are attached to a single instance as block storage. They cannot be shared between instances.
  * High Durability - EBS cannot provide super high 99.5-99.9%+ durability.

* **EBS Snapshots**
  * Snapshots are point in time backups of EBS volume stored in S3.
  * Initial snapshot contains exact copy of data on EBS volume and usually takes little longer to complete.
  * Incremental in nature and each new snapshot of initial snapshot only captures the changes since previous snapshot - saves costs, time, resources etc)
  * When deleted, blocks required to restore the other snapshots are retained.
  * Snapshots can be used in creating AMIs or create EBS volumes.
  * They are crash-consistent. Activity should be frozen on highly-transactional volumes where consistency is required.
  * Ideally for root volumes the instance should be in stopped state.
  * While EBS is AZ scoped service, snapshots in S3 are region resilient.


**AWS Documentation**

[EBS volume type](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html)
[EBS volume performance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSPerformance.html)

* * * 
[Top](#table-of-contents-)
* * * 
  
#### Instance Storage Volumes - Ephemeral

* Physical storage attached to EC2 hosts. 
* These volumes are also known as ephemeral0 to ephemeral23.
* Suscptible for hardware failures.
* Not all instances come with this type of Storage.
* Ideal patterns - 
  * Ideally should be used for non persistent data.
  * Provides high IO & through-put.
* Anti-patterns -
  * Attached to instance and cannot be scaled.
  * Cannot be shared across instances.
  * Storage is effected by Start/Stop of instances.
  * No support for snapshots and volumes are single physical disks can and do fail.

**AWS documentation**

[EC2 Instance Store](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html)

* * * 
[Top](#table-of-contents-)
* * * 

### EC2 Instance Profiles and Roles

* IAM roles - short term access credentials within AWS when used with sts:AssumeRole API call. Identities within AWS can be granted access to assume roles using that roles TRUST policy.
* Instance profiles allow a role to be assigned to a single EC2 instance, and for applications running on that instance to assume a role.
* Applications running on an EC2 instance are not 'AWS identities' and instance profiles facility to assume a IAM role.
* IAM role credentials can be obtained from EC2 instance metadata if a role is attached via an Instance profile.
http://xxx.xxx.xxx.xxx/latest/meta-data/iam/security-credentials/ROLENAME

* Only a single instance profile can be associated with an EC2 instance, containing a single EC2 role. 
* If associating a role via console, the instance profile is automatically created and associated.
* If using API's, the CLI or CloudFormation the two steps are distinct and must be done explicitly.
* Roles (via profiles) can be assigned at the time of creating the instance, or afterwards via the console, CLI or API's.
* All applications running on the instance share the role credentials - it is not possible to be more granular.


* * * 
[Top](#table-of-contents-)
* * * 

### Placement Groups

* Cluster placement groups - performance oriented
  * exists in single AZ only in closed physical vicinity.
  * highest throughput and lowest latency.
  * recreate the placement group to add additional capacity, else capacity issues could arise.
  * Use same type of instances that support place groups.
* Partition placement groups - high availability oriented.
  * Designed to spread large infrastructure sets across infrastructure in isolated fault-domains.
  * Can span AZs.
  * 7 partitions per AZ.
* Spread placement group - durability and resiliency
  * Designed for a small number of critical components where you need to ensure separation.
  * Can span AZs and have multiple instance types.

[Placement groups](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html)

* * * 
[Top](#table-of-contents-)
* * * 

### Custom Logging to CloudWatch

* By default Cloudwatch gathers all the monitoring of AWS instances.
* Cloudwatch provides access to monitoring details in each AWS instance.
* Need to install Cloudwatch agent on the EC2 instance manually using IAM role to enable custom telemetry/monitoring, Or
* Use AWS Systems Manager to install Amazon Cloud Watch Agent.

[Installing Agent](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/install-CloudWatch-Agent-on-EC2-Instance-fleet.html)

[Configuring](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-Agent-Configuration-File-Details.html)

[Creating Cloudwatch Agent Config file](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/create-cloudwatch-agent-configuration-file.html)

* * * 
[Top](#table-of-contents-)
* * * 

## Containers 

### Amazon Elastic Container Service (ECS)

* Containers are efficient way to package applications and dependencies.
* You can ensure your application runs as developer intends and is isolated from other applications.
* Applications running within a container are portable and can be migrated between platforms with minimal if any modifications.

#### ECS Architecture

1. Container definition - the part of a task definition which configured the capabilities of the container the task operates withing, the container image, the memory limits, any port mappings, storage, GPU attachments, and much more.
2. Task definition - defines the task, contains the container definitions(s). Configures how the container interacts within ECS. The network mode, the execution role, and the Launchtype. Task definitions can contain multiple containers.
3. Service - services allow additional an ECS admin to maintain a specific number of task instances within an ECS cluster. Services allow load balancing across tasks using a ELB and allow configuration of scaling and availability.
4. Cluster - are groupings of tasks and services inside ECS. They can be managed EC2 instances, or AS managed via Fargate. Self-Managed clusters can be scaled, and can use on-demand or spot pricing.

[AWS ECS documentation](https://docs.aws.amazon.com/ecs/index.html)

* * * 
[Top](#table-of-contents-)
* * * 


* * * 
[Top](#table-of-contents-)
* * * 

* * * 
[Top](#table-of-contents-)
* * * 


* * * 
[Top](#table-of-contents-)
* * * 

* * * 
[Top](#table-of-contents-)
* * * 

* * * 
[Top](#table-of-contents-)
* * * 

* * * 
[Top](#table-of-contents-)
* * * 