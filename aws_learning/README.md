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
      - [AWS official documents](#aws-official-documents)
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
    - [AWS Transit Gateway](#aws-transit-gateway)
  - [Security](#security)
    - [Account and Service Security](#account-and-service-security)
      - [AWS Key Management(KMS)](#aws-key-managementkms)
      - [AWS CloudHSM](#aws-cloudhsm)
      - [AWS Certificate Management(ACM)](#aws-certificate-managementacm)
      - [AWS Directory Service](#aws-directory-service)
    - [Network Security](#network-security)
      - [AWS Direct Connect Architecture](#aws-direct-connect-architecture-1)
   

   
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

#### AWS official documents
IAM Policy ->  https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies.html
* * * 
[Top](#table-of-contents-)
* * * 
## IAM Roles and Temporary Security Credentials 

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
[Top](#table-of-contents-)
* * * 
## AWS Accounts and AWS Organizations
### AWS Organization
* Is a service that lets you consolidate multiple AWS accounts in to a single organization - a master account/root container.
* This makes billing and permissions easier and allows for the creation of managed accounts. 
* Can be further split in to Organization units(OU) which contains accounts - like one OU for each business unit.
* Can be operated in either 'Consolidated Billing' or 'All Features' mode.
* * * 
### Service Control Policies
Service control policies when applied directly or indirectly to AWS accounts define what actions can be performed on what services within that account.
These policies do not actually grant the permissions. They only restrict what you can do if you have permissions. Usually can be used to whitelist or blacklist services.

If multiple SCPs apply to an account, only the overlap of those SCPs is permitted.


* JSON doc that can be directly applied to a AWS account/OU.
* Inherits downwards.
* SCPs have no effect on master account.
* Avoid using master accounts for any AWS services. Use it only for billing and user store. You cannot place any restrictions on the resources using service control policy.

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
Provides the abilit to implements IT Service Catalog in AWS. Usually used for larger organizations that have formal IT processes.

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
Use a non AWS user id to login and use AWS resources. This is similar to using a in house/active directory security domains ids for logging in to AWS. Like using your company email id as AWS login details.

Google, Facebook, Twitter are external identity providers(IDPs). They identiy and authenticate the users. STS provides the temporary credetials that will be used for interacting with AWS resources/services.
* * * 
[Top](#table-of-contents-)
* * * 
### IAM Permissions Boundaries
* * * 
[Top](#table-of-contents-)
* * * 
### Policy Evaluation Logic
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
* VPC router is controlled by route tables. VPCs come with a default 'MAIN' Route table. Customer RTs can be defined and attached to subnets
* Route tables contain a default 'local' route 
* A route matches a destination and tells the VPC router where to direct IP traffic. More specific routes take priority(i.e /32 > /16).
* VPC routers are used for VPC endpoints, VPC peering connections, Egress only Internet gateway, Internet gateway, NAT-Gateway.

* * * 
[Top](#table-of-contents-)
* * * 
### Network Access Control Lists (NACLs)
NACLs are firewalls attached to VPC subnets. They filter IP traffic entering or leaving the subnet. NACLs are STATELESS which means ephemeral port rules are required to allow 'response' traffic.
* A subnet can have one associated NACLs acting as a barrier between VPC and its subnet.
* VPCs have a defailt NACLS associated with any subnets in that VPC by default.
* Inbound rules are applied for traffic coming in to subnets.
* Outbound rules are applied for traffic coming out of the subnets.
* Rules priority is done based on Rule # field. Lowest Rule # will take higher priority over a higher Rule # entry.
* Rules are based on IP address ranges only, and cannot refer any logical resources.
* Common use case for NACLs - Whitelist/Blacklist traffic from/to an IP.
* NACLs does not effect traffic between two EC2 instances with in same Subnet. They come in to effect only when the traffic is flowing in to/out of a Subnet.
* NACLs are the only option when Security groups cannot be used to restrict the routing. 

[Wiki for Ephemeral port](https://en.wikipedia.org/wiki/Ephemeral_port)
* * * 
[Top](#table-of-contents-)
* * * 
  
### Security Groups (SG)

SG companion security filtering products in AWS, applied to networks inside VPC. SGa are applied to network resources and effect the traffic coming in/to them.

* Every VPC comes with a default SG
* Each SG contains inbound/outbound rules for IP traffic.
* SG procesing has NO order - all rules are executed at once. There is a deafult implicit DENY. SG's cannot explicitly DENY.
* SG rules are STATEFUL. If traffic is allowed IN, it's corresponding return traffic is automatically allowed - this cannot be changed. The same applies to outbound traffic, its return communications are automatically permitted. ==> You do not have to worry about ephemeral ports.

* * * 
[Top](#table-of-contents-)
* * * 
  
### Public vs Private Subnets, Internet Gateways, and IP addressing

* A private subnet is a subnet with default configuration. It cannot communicate with public internet or AWS public zone networks.
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
* One solution is to use EC2 instances as DNS relays that let the on premise instances to talk to instances in VPC indirectly.
* Inbound/Outbound endpoints configuration in R53 resolver does the DNS resolving between VPC and on-prem/external/non-VPC networks.

[AWS documentation](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver.html)
* * * 
[Top](#table-of-contents-)
* * * 

### VPC Flow Logs

* Provides network traffic visibility (logging and monitoring toolset).
* Stores only Metadata, but not application data.
* **NOT LOGGED -** DHCP traffic, AWS DNS, Internal AWS instances' Metadata, License Activation Requests.
* Collects data at one of the 3 levels:
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
* SGs can reference groups in remove VPC's. SGs and NACLs can also reference CIDR/IP.
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