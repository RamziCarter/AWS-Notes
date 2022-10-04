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










