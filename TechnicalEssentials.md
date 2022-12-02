# Technical Essentials Modules

__6 Advantages of cloud computing__
1. Pay as you go 
1. benefit from massive economics of scale
1. stop guessing capacity
1. increased speed and agility
1. realize cost savings
1. Global in minutes
---
<!-- Comments -->

**Storage** in AWS stores in a data center 
* aws clusters datacenters together which are linked together (__Infrastructure__)
```
  * data centers
  * redundant and high speed low latency links
  * availability zones
  * regions
```

#### AWS Region Considerations
* Compliance
* Latency
* Pricing
* Service Availibility

#### Scope of AWS Services
* Availibility zone
* region
* Global
---
#### API - Application Programmiong Interface

Ways to interact with AWS API
* AWS Management Console
* AWS Command Line Interface
* AWS Software Development Kits
---

#### AWS Security - **Shared Responsibility Model**

> Customer
* Security in the cloud
* Customer Data
* Platform, Applications, Identity, Access Management
* Operating System, Network, Firewall configuration

* __Client-side__: 
  * Data Encryption, Integrity, Authentication
* __Server-side__: 
  * Encryption, File System and/or Data
  * Network Traffic Protection:
  * Data Encryption, Integrity, Authentication

> AWS
* Security in the Cloud
  * Compute
  * Storage
  * Database
  * Networking
  * Hardware/AWS Gloabal Infrastructure
  * Regions
  * Availability Zones
  * Edge Locations
 ---
 
 #### Account Safety
 
Protect **Root User**!!!! (Email: **Access to all the capabilities**)
* SFA - Single-Factor Authentication
* MFA - Multi-Factor Authentication

> Authentication - "Are you who you say you are?"

> Authorization - "What actions can you perform?"
 
#### Multi-Factor Authentication Categories
1. Something you know: Username/Password
1. Something you have: One-time Password
1. Something you are: Fingerprint/Face-ID

---
#### IAM - Identity and Access Management

* IAM Policies - __Grant or Deny permissions__

> Structure of IAM Policies

```bash
{
 "Statement": [{
   "Effect": "Allow",
   "Action": "eC2: *",
   "Resource": 
   "Condition": {
   
   }
  }]
  }
```
* IAM Policies can be assigned to users and groups 
* The users/groups either have/don't have permission to given parameters
* IAM Policies are usually stored within .JSON documents

#### Policy Structure

|Element|Description|Required|Example|
|-------|-----------|--------|-------|
|Effect|Specifies whether the statement results in an allow or an explicit deny| ✔️|"Effect": "Deny"| 
|Action|Describe the specific action that will be allowed or denied| ✔️|"Action": "iam": "CreateUser"|
|Resource|Specifies the Object or Objects that the statement covers| ✔️|"Resource": "arn: aws:iam:: account-ID-without-hyphens:user/Bob"|

---

#### Role Based Access om AWS
1. Admin creates IAM Role that grants access to the Amazon S3 Bucket
1. Launch EC2 Instance with IAM Role
1. App retireves IAm Role Credemtials from EC2
1. App makes API call using temporary credentials


#### Scope By Level!!
```
                AWS Account                        | Billing, IAM, Route53
                 IAM Users
                   |
     --------------------------------    
     |               |              |              | S3, DynamoDB, VPC, ELB
  Region 1        Region 2      Region 3   
     |               |              |
    / \             / \          /  |  \
 AZ1  AZ2        AZ1  AZ2      AZ1  AZ2  AZ3       | EC2, RDS, EBS
 
```
---

#### AWS Services General Overview (Not all Services, Just Most Common)
> AWS Compute and Analytics Services
* EC2 - Elastic Compute Cloud
* Auto Scaling - EC2 Horizontal Scaling
* Lambda - Serverless Computing
* ELB - Elastic Load Balancer
* ECS - Eleastic Container Service
* EMR - Elastic Mapreduce
* Kinesis - Real Time Data/Video Streaming
* Athena- Interactive Query Engine
* QuickSight - Business Intelligence
* Glue - ETL Service

> AWS Storage and Database Services
* EBS - Elastic Storage Block
* S3 - Simple Storage Service
* EFS - Eleastic File System
* RDS - Relational Database Service
* DynamoDB - AWS NoSQL Database
* RedShift - Data Warehousing
* Elasticache - Fast and Flexible Caching

> AWS Network and Management Services
* VPC - Virtual Private Cloud
* Route53 - AWS DNS Service
* Direct Connect - Dedicated Network
* Cloud Front - Content Delivery Network
* CloudWatch - Application & Infrastructure monitoring
* CloudFormation - Provision Infrastructure
* Elastic Beanstalk - Application Orchestration Service
* Opsworks - Infrastructure Configuration Management

> AWS Application and Development Services
* API Gateway - Managed REST and Websocket API's
* SQS - Simple Queue Service
* SNS - Simple Notification Service
* SES - Simple Email Service
* Cognito - User Management for Web & Mobile Apps
* CodeCommit - Hosted GIT Repository by AWS
* CodeBuild - Continuos Integration Service
* CodeDeploy - Automated Deployment
* CodePipeline - Continous Delivery Service
* CodeStar - Develop Build Deploy Manage and Track

---

#### Role Based Access in AWS

> Root User - Access to all resources within account
* best to lock down this user
  * delete root user access keys
  * enable MFA

> Follow Principle of least Privilege 
* grant only the necessary permissions to do a particular job
* IAM Policiy 
  * Grant additional permissions if necessary by user, group or role


> Correct IAM Usage
* create and manage users/groups/roles

> Use IAM Roles when possible
* when roles are assigned, IAM dynamically provides temporary credentials that expire from 15 mins to 36 hours
* IAM users have long term credentials in the form of username and password combinations or a set of access keys 
  * keys only expire when admin rotates them
  * passwords may be rotated as well

> Use and Identify Provider
* provides a single source of truth for all identities in your organization

> AWS Single Sign-On
* an identity provider that lets your users sign into a user potal with a single set of credentials
  * it then provides users access to their assigned accounts and applications in a central location

> Abilities of AWS SSO
* Like IAM
  * directories to create users 
  * organize them into groups
  * set permissions across the groups
  * grant access to AWS resources
* Advantages over IAM
  * if you're using a 3rd party identity provider you can sync your users and groups to AWS SSO
    * no need to recreate users that exist elsewhere
    * manage users frim your identity provider (IdP)
    * AWS SSO separates the duties between your IdP and AWS (not inside or dependent of IdP)
    
---
  
#### Learning about AWS Services

EC2 Instance Demo 
* AWS provides a default VPC
* VPC is a private network for AWS resources (Virtual Private Cloud)

```
EVERY EC2 MUST LIVE INSIDE OF A NETWORK
```

* An instance of EC2 is one single virtual machine

> Servers 
* handle HTTP - **Hyper Text Transfer Protocol**
  * requests and send responses to clients following the client-server model
  
#### 3 Types of compute options
* virtual machines
* container services
* serverless

> AMI - Amazon Machine Image
* Root volume template
  * Typically contains an OS
  * Applications pre-installed on instance at boot
  * Launch permissions
  * Block device mapping

---
The amazon machin image looks like this:

```
An Amazon Machine Image (AMI) is a supported and maintained image provided by AWS that provides the information required to launch an instance.
```

An AMI includes the following:

One or more Amazon Elastic Block Store (Amazon EBS) snapshots, or, for instance-store-backed AMIs, a template for the root volume of the instance (for example, an operating system, an application server, and applications).

Launch permissions that control which AWS accounts can use the AMI to launch instances.

A block device mapping that specifies the volumes to attach to the instance when it's launched.

Amazon Machine Image (AMI) topics


