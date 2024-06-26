# Note

## AWS

- AWS Cloud History
  ![alt text](image-104.png)

- AWS Infrastructure
  https://aws.amazon.com/about-aws/global-infrastructure/regions_az/

- AWS Region
  - AWS has Regions all aounrd the world
  - Names can be us-east-1, eu-west-3...
  - A region is a cluster of data centers
  - Most AWS services are region-scoped

- How to choose an AWS Regions?
  - Compliance with data govermance and legal requirements: data never leaves a region without your explicit permission
  - Proximity to customers: reduced latency
  - Ava services within a Region: new services and new features aren't available in every Region
  - Pricing: pricing veries region to region and is tranparent in the service pricing page

- AWS Availability Zones
  - Region region has many availability zone (usually 3, min is 3, max is 6).
    - ap-southeast-2a
    - ap-southeast-2b
    - ap-southeast-2b
  - Each availablity zone (AZ) is one or more discrete data centers with redundant power, networking,  and connectivity
  - They're seperate from each other, so that they're isolated from disasters
  - They're connected with high bandwidth, ultra-low latency networking 
  ![alt text](image-105.png)

- AWS Points of Presence (Edge Locations)
  - Amazon has 400+ Points of Presence (400+ Edge Locations & 10+ Regional Caches) in 90+ cities across 40+ countries)
  - Content is delivered to end users with lower latency
  ![alt text](image-106.png)  

- Tour of the AWS Console
  - AWS has Global Services
    - Identity and Access Management (IAM)
    - Route 53 (DNS service)
    - CloudFront (Content Delivery Network)
    - WAF (Web Applicaton Firewall)
  - Most AWS services are Region-scoped
    - Amazon EC2 (Infrastructure as a Service)
    - Elastic Beanstalk (Platform as a Service)
    - Lambda (Function as a Service)
    - Rekognition (Software as a Service)
  - Region Tablle: https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/?nc1=h_ls

- Tour of the AWS Console hands on
  - Switch region (Global or Regional)
  - Console Home
  - Services > All services
  - Services> Search services

- About the UI Changes in the course

## IAM

### IAM: Users & Groups

- IAM: Users & Groups
  - IAM = Identity and Access Management, Global service
  - Root account created by default, shouldn't be used or shared
  - Users are people within your origanization, and can be grouped
  - Groups only contain users, not other groups
  - Users don't have to belong to a group, and user can belong to multiple groups
  ![alt text](image-107.png)

- IAM: Permissions
  - Users or Groups can be assigned JSON documents called policies
  - These policies define the permissions of the users
  - In AWS you apply the least privilege principle: don't give more permissons than a user needs
  ![alt text](image-108.png)

- IAM: Users & Groups Hands on
  - Add user
    - Add user to group
      - Create group 

  - Account Alias
    - Create alias for AWS ccount


- IAM Policies inheritance
  ![alt text](image-109.png)

- IAM Policies Structure
  - Consists of
    - Version: policy language, always include "2012-10-17"
    - Id: an identifier for the policy (optional)
    - Statement: one or more individual statements (requried)
  - Statements consists of
    - Sid: an identifier for the statement (optional)
    - Effect: whether the statement allows or denies access (Allow, Deny)
    - Principal: account/user/role to which this policy applied to
    - Action: list of actions this policy allows or denies
    - Resource: list of resources to which the actions applied to
    - Condition: condtions of when this policy in effect (optional)
  ![alt text](image-110.png)

- IAM Policies Hands on
  - Users > Add permissions
    - Attach existing policies directly
  - User Groups > Create group
  
- Policies
  - Permissions 
    - Policy summary
    - JSON
  - Create polcy

- IAM - Password Policy
 - Strong passwords = higher security for your account
 - In AWS, you can setup a password policy
  - Set a minimum password length
  - Require specific character length
    - including uppercase letters
    - lowercase letters
    - numbers
    - non-alphanumeric characters
  - Allow all IAM users to change their own passwords
  - Require users to change their password after some time (password expiration)
  - Prevent password re-use

- Multi Factor Authentication - MFA
  - Users have access to your account and can possibly change configurations or delete sources in your AWS account
  - You want to protect your Root Accounts and IAM users
  - MFA: password you know + security device you own
    ![alt text](image-111.png)
  - Main benefiit of MFA
    if a password is stolen or hacked, the account is not compremised

- MFA devices options in AWS
  - Virtual MFA device
  - Universal 2nd Factor (U2F) Security Key
  ![alt text](image-112.png)
  - Hardware Key Fob MFA Device
  - Hardware Key Fob MFA Device for AWS GovCloud (US)
  ![alt text](image-113.png)

- IAM MFA Hands on
  - Account settins > Password Policy
    - Set password policy

  - Your Security Credentials
    - Multi-factor authentication (MFA)
      - Activate MFA
        - Virtual MFA device
        - U2F security key
        - Other hardware MFA device

- AWS Access Keys and SDK
  - To access AWS, you have three options
    - AWS Management Console ()
    - AWS Command Line Interface (CLI):
    - AWS Software Developer Kit (SDK): for code: protected by access keys
  - Access Keys are generated through the AWS Console
  - Uesr manage their own access key
  - Access Keys are secret, just like a password, Don't share them
  - Access Key ID ~= username
  - Secret Access Key ~= password

- What's the AWS CLI?
  - A tool that enables you to interact with AWS services using commands in your command-line shell
  - Direct access to the public APIs of AWS services
  - You can develop scripts to manage your resources
  - It's open-source
  - Alternative to using AWS Management Console

- What's the AWS SDK?
  - AWS Software Development Kit (AWS SDK)
  - Language-specific APIs (set of libraries)
  - Enables you to access and manage AWS services progmrammatically
  - Embedded within your application
  - Supports
    - SDKs (JavaScript, Python, PHP, .NET, Ruby, Java, Go, Node.js, C++)
    - Mobile SDKs (Android, iOS,...)
    - IoT Device SDKs (Embedded C, Arduino,...)
  - Example: AWS CLI is built on AWS SDK for Python
  ![alt text](image-114.png)

### AWS CLI Setup

- AWS CLI Setup on Windows
- AWS CLI Setup on MacOS
- AWS CLI Setup on Linux
- Create Access Keys
  - Users > ${username} > Security credentials

### AWS CloudShell

- AWS CloudShell
  - command line usage
    - aws
  - Preferences
    - Font
    - Theme
  - Download file
  - Upload file
  - Tabs layout  


### IAM Roles for Services

- IAM Roles for Services
  - Some AWS service will need to perform action on your behale
  - To do so, we will assign permissions to AWS services with IAM Roles
  - Common roles
    - EC2 Instances Roles
    - Lamdba Function Roles
    - Roles for CloudFormation
  ![alt text](image-115.png)

### IAM Role Hands on

- Roles > Create Role
  - AWS Service 
    - Choose a use case: EC2 Instance
    - IAMReadOnlyAccess

### IAM Security Tools

- IAM Credentials Report (account-level)
  - a report that lists all your account's users and the status of their various credentials
- IAM Access Advisor (user-level)
  - Access advisor shows the service permissions granted to a user and when those services were last accessed
  - You can use this information to revise your policies

### IAM Security Tools Hands on

- Credential report > Download Report
- Users > ${username} > Access Advisor


### IAM Best Practices

- IAM Guidelines & Best Practices
  - Don't use the root account except for AWS account setup
  - One physical user = One AWS user
  - Assign users to groups and assign permissions to groups
  - Create a strong password policy
  - Use and enforce the user of Multi Factory Authentication (MFA)
  - Crate and user Roles for giving permissions to AWS services
  - Use Access Keys for Promgrammatic Access (CLI/SDK)
  - Audit permissions of your account with IAM Credenitals Report
  - Never share IAM user & Access Keys

### IAM Summary

- IAM Section - Summary
  - Users: mapped to a physical user, has a password for AWS Console
  - Groups: contains users only
  - Policies: JSON doucment that outlines permissions for users or groups
  - Roles: for EC2 instances or AWS services
  - Security: MFA + Password Policy
  - Access Keys: access AWS using the CLI or SDK
  - Audit: IAM Credential Reports & IAM Access Advisor

## Budget

- AWS Budget Setup
  - My Account > IAM User and Role Access to Billing Information
    - Activate IAM access (enabed)
  - Billing > Bills
  - Billing > Free tier
  - Billing > Budgets
    - Budget setup
      - Use a template
      - Customize
    - Template - new
      - Zero spend budget
      - Monthly cost budget
        - Enter your bedgeted amount ($)
      - Daily savings Plans coverage budget


## EC2 Section

### EC2 Basics

- EC2 is one of the most popular of AWS' offering
- EC2 = Elastic Compute Cloud = Infrastructure as a Service
- 

### EC2 Basics

- Instance Type
- EC2 User Data
- Storage
  Size
  Delete on Termination
- Tags
  - Instances
  - Volumes
  - Network Interfaces
- Security Group
  Type
  Protocol
  Source: 0.0.0.0/0 anywhere
- Key Pair
  The key file is only show once in this step.
- Public IPv4 Address
- Private IPv4 Addresses

- Instance State
  - Stop Instance
  - Terminate Instance
  - Start Instance


## EC2 Instance Types

### Overview

- Naming
  - m: instance class
  - 5: generation (AWS Improved them over time)
  - 2xlarge: size within the instance class

- General Purpose
  - t2.micro
- Compute Optmized
  - C6g
  - HPC
  - Media transcoding
  - ML
  - Gaming Server
- Memory Optimized
  - R6g
  - BI
- Storage Optimized
  - i3
  - i, G, H

- Accelerated Computing
- Instance Featuers
- Measuring Instance Performance


### Security Groups

- Security Groups only contain allow rules
- Security Groups rules can reference by IP or by security group

### Deeper Dive

- Acting as a 'firewall' on EC2 Instances
- They regulate:
  - access to ports
  - authorised IP ranges - IPv4 and IPv6
  - Control of inbound network(from other to the instace)
  - Control of outbound network (from the instace to other)

### Good to know

- Can be attched to multiple instances
- Locked down to a region/VPC combination
- Does live 'outsie' the EC2 - if traffice is blocked the EC2 isntacne won't seet it
- It's good to maintain one separate security group for SSH access
- If your application is not accessible (timeout), then it's a security group issue.
- If your application gives a 'connection refused' error, then it's an applcation error or it's not launched
- All inbound traffice is blokced by default


### Classic Ports to know

- 22 = SSH
- 21 = FTP
- 22 = SFTP
- 80 = HTTP
- 443 = HTTPS
- 3389 = RDP


### SSH Summary Table

![alt text](image.png)


### Which Lectures to watch

- Mac / Linux:  SSH
- Windows: Putty Lecture
- Windows 10: SSH on Windows 10 lecture
- All: EC2 Instance Connect lecture

If things don't work...
- Re-watch the lecture. You may have missed someting
- Read the troubleshooting guide
- Try EC2 Instance Connect


### IAM Role for EC2 Instance

- EC2 Instance > Seucrity > Security details > IAM Role


### EC2 Instances Purchasing Options

- On-Demand Instances
  - Pay for what use
  - Has the highest cost but no upfront payment
  - No long-term commitment
  - Recommended for short-term and un-interrupted worloads, where you can't predict how the application will behave
- Reserved: minimum 1 year
  - Reserved Instance
    - Up to 75 discount compared to on-demand
    - Reservation period: 1 year = + discount | 3 years = +++ discount
    - Purchasing options: no upfront | partinal upfront = +| All upfront = ++discount
    - Reverse a specfic instance type
    - Recommended for steady-state usage applcations (think databae)
  - Covertaible Reserved Instance
    - can change the EC2 instace type
    - Up to 54% discount
  - Scheduled Reserved Instances
    - launch within time window you reserve
    - When you require a fraction of day/week/month
    - Still commitment over 1 to 3 years
- Spot Instances
  - Cat get a discount of up to 90% compared to On-demond
  - Instaces that you can 'lose' at any point of time if your max price is less thean the cruuent spot price
  - The most cost-efficient instances in AWS
  - Useful for workflows that are resilient to failure
  - Not suitable for critical jobs or databases
- Dedicated Host: book an entire physical server, control instance placement
  - An amazson EC2 Dedicated Host is a physical server with EC2 instance capacity fully dedicated to your use. Dedicated Hosts can help you address compliacne requirements and reduce costs by allowing you to use your existing server-bound software licenses.
  - Allocated fro your account for a 3-years period reservation
  - More expensive
  - Useful for software that have complicated licensing model(BYOL - Bring Tour Own License)
  - Or for companies that have string regulatory or compliance needs
- EC2 Dedicated Instances
  - Instances running on hardware that's dedicated to your
  - May share HW with other isntances in same account
  - No control over instance placement (can move hw after stop/start)
    ![alt text](image-1.png)

- Price Comparision


### EC2 Spot Instance Requests

- EC2 Spot Instance Requests
  - Can get a discount of up to 90% compared to On-demond
  - Define max spot price and get the instance while current spot price < max
    - The hourly spot price varies based on offer and capacity
    - If the current price > your max price you can choose to stop or terinate your instance with a 2 minutes grace period
  - Other strategy: Spot Block
    - 'block' spot instance during a specified time frame (1 to 6 horus) without interruptions
    - In rare sisuations, the instance may be reclaimed
  - Used for batch jbos, data analysis, or workloads that are resilient for failures
  - Not great for critical jobs or databases

- EC2 Spot Instsances Pricing
  [Pricing](https://.../ec2sp/v1/spot/home?region=us-east-1)

- How to terminate Spot Instances
  ![alt text](image-3.png)

- Spot Fleets
  - Spot Fleets = set of Spot Instances + (optional) On-Demond Instances
  - The Spot Fleet will try to meet the target capacity with price constraints
    - Define possible launch pools: instance type (m5.large), OS, Availability Zone
    - Can have multiple launch pools, so that the fleet can choose
    - Spot Fleets stops launching instances when reaching capacity or max cost
  - Strategies to allocated Spot Instances:
    - lowestPrice:
    - deversifiend:
    - capacityOptimized
  - Spot Fleets allow us the auto request Spot Instances wiht the lowest price

### EC2 Spot Instance Launch Types Hands On

- [045 EC2 Instances Launch Types Hands On_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1wR4y1F7YM/?p=40&spm_id_from=pageDriver&vd_source=b12b77fc1ee1a9f1bd40e7d3802aa43c)


### Private vs Public IP (IPv4)

- Private vs Public IP (IPv4)
  - Sorts of IPs. IPv4 and IPv6
  - IPv4 allows for 3.7 billion 

- Public IP
  - Can be geo-located easily
- Private IP

- Elastic IPs
  - 5 elastic IP
  - try to avoid using Elastic IP


### Placement Groups

- Placement Groups
  - You want control over the EC2 Instance placement strategy
  - The strategy can be defined using placement groups
  - When you create a placement group, you specify one of the following strategies for the group
    - Cluster - clusters instances into a low-latency group in a single AZ
      ![alt text](image-4.png)
    - Spread - spreads isntances across underlying hw (max 7 isntances per group per AZ) - critical applcations
      ![alt text](image-5.png)
    - Partition - spreads instances across many different partitions (which repy on diffrenet sets of racks) within an AZ. Scales to 100s of EC2 isntaces per group.
      ![alt text](image-6.png)


### Elastic Network Interface (ENI)

- Elastic Network Interface (ENI)
  - Logical compoenet in a VPC that represents a virtual network card
  - The ENI can have the following attributes
    - Primary private IPv4, one ore more secondary IPv4
    - One Ealstic (IPv4) per private IPv4
    - One Public IPv4
    - Onre are more security groups
    - A MAC address
  - You can create ENI independently and attach them on the fly (move them) on EC2 instances for failover
  - Bound to a specific AZ

### EC2 Hibernate

- EC2 Hibernate
  - EC2 status
    - Stop:
    - Terminate: EBS is destroyed
  - On start
    - First start: the OS boot & the EC2 user Data scripts is run
    - Following starts: the OS boots up
- Intrudcing EC2 Hibernate
  - The in-memory state is preserved
  - The instance boot is much faster
  - Under the hood: the RAM state is written to a file in the root EBS volume
  - Thr oot EBS volume must be encrypted
- Use cases
  - long-running processing
  - saving the RAM state
  - services that take time to intialize
-  Good to know
  - Supported instance families
  - Instance RAM size- must less than 150 GB
  - Instance size: not supported for bare metal instances
  - AMI: all AMIs
  - Root Volume: must be EBS
  - Available for On-Demond and Reserved instances
  - An instance cannot be hibernated more than 60 days.


### EC2 Hibernate Hands on

- EC2 Hibernate
  - Enable hibernation as an additinal stop behavior
  - Ensure hibernate is working
    - Hibernate the instace
      - Use `uptime` to check hibernation


### EC2 Nitro

- EC2 Nitro
  - Underlying Platform for the next neneration of EC2 instances
  - New virtualization technology
  - Allow for better performance
    - Better networking options(enhanced networking, HPC, IPV6)
    - Higher Speed EBS (64000 EBS IOPS - max 32000 on no-Nitro)
  - Better underlying security
  - Instance types example:
    - Virtualized: 
    - Bare metal:
- EC2 - Understanding vCPU
  - Multiple threads can run on one CPU (multithreading)
  - Each treahd  is represented as virtual CPU (vCPU)
  - Example: m5.2xlarge
    - 4 CPU
    - 2 threads per CPU
    - => 8 vCPU in total
    ![alt text](image-7.png)
- EC2 - Optimzing CPU options
  - EC2 isntances come with a combination of RAM and vCPU
  - But in some cases, you may want to change the vCPU options:
    - \# of CPU cores: you can decreast it (helpful if your need high RAM and low number of CPU) - to decrease licensing costs
    - \# of threads pe00000000000r core: disable multithreading to have 1 thread per CPU - helpful for high performance computing (HPC) workloads
  - Only speficfied during instance launch
  ![alt text](image-8.png)

- EC2 - Capacity Reservations
  - Capacity Reservations ensure your have EC2 Capacity when needed
  - Manual or planned end-date for the revervation
  - No need for 1 or 3-year commitment
  - Capacity access is immediate, you get billed as soon as it starts
  - Specify
    - The AZ in which to to rerve the capcity (only one)
    - The number of instances for which to reserve capacity
    - The instance attributes, including the instance types, tenancy and platform/OS
  - Combine with Reserved Instaces and Savings Plans to do cost saving
  ![alt text](image-9.png)

## EC2 Instance Storage
- EC2 Instance Storage Section
  - What's EBS Volume
    - is a network drive you can attach to your instances while they run
    - allows your instances to persists data, even after their termination
    - can only be mounted to one instance at a time(at the CCP level)
    - The are bound to specific AZ
    - Analogy: Think of them as a 'network USB stick'
  - EBS Volume
    - It's a network drive (not a physical drive)
      - It uses the network to communicate the instance, which means there might be a bit of latency
      - It can be deatched from an EC2 instacne and attached to another one quickly
    - It's locked to an AZ
      - An EBS Volume in us-east-1a cannot be attached to us-east-1b
      - To move a volume across, you first need to snapshot it
    - Have a provisioned capacity (size in GBs, and IOPS)
      - You get billed for all the provisioned capacity
  - EC2 Volume - Example
    ![alt text](image-10.png)
  - EBS - Delete on termination attribute
    - Controls the EBS behaviour when an EC2 instance terminates
      - By default, the root EBS volume is deleted
      - By default, any ohter attached EBS vloume is not deleted
    - This can be controlled by the AWS console/AWS CLI
    - Use case: persrve root volume when instance is terminated
    ![alt text](image-11.png)
   - EBS Volume Hands on
    - Create a volume
    - Attach the volume to an existed EC2 instance
    - Create the new EC2 instance from the volume
    - Delete the volume

## AMI
- AMI Overview
  - AMI = Amazson Machine Image
  - AMI are a customization of EC2 instance
    - You add your own software, configuration, operation system, monitoring...
    - Faster boot / configuration time because all your software is pre-packaged
  - AMI are build for specific region (and can be copied accross regions)
  - You can launch EC2 instances from
    - A public AMI: AWS provided
    - Your own AMI: you make and maintain them yourself
    - An AWS Marketplace AMI: an AMI someone else made (and potentially sells)

- AMI Process (from an EC2 instace)
  - Start an EC2 instance and customize it
  - Stop the instance (from dataw integrity)
  - Build an AMI - this will also create EBS snapshots
  - Launch instances from other AMIs
  ![alt text](image-12.png)

- AMI Hands on
  - EC2 user data
  - Launch an EC2 instance
  - Create an AMI image from an EC2 Instance

## EC2 Instance Store

- EC2 Instance Store
  - EBS volumes are network drives with good but "limited" performance
  - If you need a high-performance hardware disk, use EC2 Instance Store
  - Better I/O Performace
  - EC2 Instance Store lose their storage if they're stopped (ephemeral)
  - Good for buffer / cache / scratch data / temorary content
  - Rick of data loss if hardware fails
  - Backups and Replication are your responsibility

- Load EC2 Instance Store
  ![alt text](image-13.png)

## AWS EC2 Instance Metadata

- AWS EC2 Instance Metadata
  - AWS EC2 Instance Metadata is powerful but one of the least known features to developers
  - It allows AWS EC2 instances to "learn about themselves" without using an IAM Role for that purpose
  - The URL is http://169.254.169.254/latest/meta-data
  - You can retrieve the IAM Role name from the metadata, but you CANNOT retrieve the IAM Policy
  - Metadata = Info about the EC2 instance
  - Userdata = launch script of the EC2 instance

  ```
  curl http://169.254.169.254/latest/meta-data
  ```

## AWS SDK Overview

- AWS SDK Overview
  - What if you want ot perform actions on AWS directly from your applications code> (without using the CLI)
  - You can use an SDK (software development kit)
  - Official SDKs are
    - Java
    - .NET
    - Node.js
    - PHP
    - Python
    - Go
    - Ruby
    - C++

  - We hav to use the AWS SDK when coding against AWS Services such as DynamoDB
  - The AWS CLI uses Python SDK
  - The exam expects you to know when you should use an SDK
  - We'll practice the AWS SDK when we get to the Lambda functions
  - If you don't specify or configure a default region, then us-east-1 will be chosen by default

## EBS
- EBS Volume Types
  - EBS Volumes come in 6 types
    - gp2 / gp3 (SSD)
    - io1 / io2 (SSD)
    - st1 (HDD)
    - sc1 (HDD)
  - EBS Volumes are characterized in Size | Throughput | IOPS (I/O Ops Per Sec)
  - When in doubt always consult the AWS documentation - it's good
  - Only gp2/gp3 and io1/io2 can be used as boot volumes
 
- EBS Volume Types Use cases
  - General Purpose SSD
    - Cost effective storage, low-latency
    - System boot volumes, Virtual desktops, Development and test environments
    - 1GiB - 16 Tib
    - gp3
      - Baseline of 3000 IOPS and throughtput of 125 MiB/s
      - Can increase IOPS up to 16000 and throughput up to 1000 MiB/s independently
    - gp2
      - Small gp2 volumes can burst IOPS to 3000
      - Size of the volume and IOPS are linked, max IOPS is 16000
      - 3 IOPS per GB, means at 5334 GB we are at max IOPS
  - Provisioned IOPS (PIOPS) SSD
    - Critical business applications with sustained IOPS performance
    - Or applications that need mroe than 16000 IOPS
    - Create for database workloads (sensitive to storage perf and consitency)
    - io1/io2 (4 GiB -  16 TiB)
      - Max PIOPS: 64000 for Nitro EC2 instances & 32000 for other
      - Can increate PIOPS independently from storage size
      - io2 have more durabilty and more IOPS epr GiB (at the same price as io1)
    - io2 Block Express (4 GiB - 16 TiB)
      - Sub-milisecond latency
      - Max PIOPS: 25600 with an IOPS: GiB ration of 1000:1
    - Support EBS Multi-attach
  - Hard Disk Drives (HDD)
    - Cannot be a boot volume
    - 245 MiB to 16 TiB
    - Throughput Optimized HDD (st1)
      - Big Data, Data warehouses, Log Processing
      - Max Throughput 500 MiB/s - max IOPS 500
    - Cold HDD (sc1):
      - For data that is infrequently accessed
      - Scenarios where lowest cost is important
      - Max throughput 250 MiB/s - max IOPS 250
  ![alt text](image-14.png)

- EBS Multi-Attach - io2/io3 family
  - Attach the same EBS volume to multiple EC2 isntances in the same AX
  - Each isntance has full read & write permissions to the volume
  - Use case
    - Archieve higher applcation availability in cloustered Linux applications (exL Teradata)
    - Applications must manage concurrent write operations
  - Must us a file system that's clsuter-sware (not XFS, EX4, etc...)

- EBS Encryption
  - When you create an encrypted EBS volume, you get the following
    - Data a rest is encrypted inside the volume
    - All the data in flight moving between the instance and the volume is encrypted
    - All snapshot are encrypted
    - All volumes created from the snapshot
  - Encryption and decryption are handled trasparently (you have nothing to do)
  - Encryption has minimal impact on latency
  - EBS Encryption leverages keys from KMS (AES-256)
  - Copying an unencrypted snapshot allows encryption
  - Snapshots of encrypted volumes are encrypted

- Encryption: encrypt an unencrypted EBS volume
  - Create an EBS snapshot of the volume
  - Encrypt the EBS snapshot (using copy)
  - Create new EBS volume from the snapshot (the volume will also be encrypted)
  - Now you can attach the encrypted volume to the original instance

## EFS
- EFS - Elastic File System
  - Managed NFS (network file system) that can be mounted on many EC2
  - EFS works with EC2 instance multi-AZ
  - Highly available, scalable, expensive (3x gp2), pay per use
  - Use cases: content management, web serving, data sharing, wordpress
  - Use NFSv4.1 protocol
  - Uses security group to control access to EFS
  - Compatible with Linux based AMI (not Windows)
  - Encryption at rest using KMS
  - POSIX file system (~Linux) that has a standard file API
  - File system scales automatically, pay-per-use, no capacity planning
  ![alt text](image-16.png)

- EFS - Performance & Storage Classes
  - EFS Scale
    - 1000s of concurrent NFS clients, 10 GB+/s throughput
    - Grow to petabyte-scale network file system, automatically
  - Performance mode (set at EFS creation time)
    - General purpose (default): latency-sensitive use cases (web server, CMS, etc...)
    - Max I/O - higher latency, throughtput, highly parallel (big data, media processing)
  - Throughput mode
    - Bursting (1TB = 50MiB/s + burst of up to 100 MiB/s)
    - Provisioned: set thorughput regardless of storage size, ex: 1GiB/s for 1TB storage
  - Storage Tiers (lifecycle management feature = move file after N days)
    - Standard: for frequently accessed files
    - Infrequent access (EFS-IA): const to retrieve files, lower price to store
- EFS hands on
  - Create EFS shared the data data between 2 EC2 instance

- EBS vs EFS - Elastic Block Storage
  - EBS volumes
    - can be attached to only one instance at a time
    - are locked at the AZ level
    - gp2: IO increases if the disk size increases
    - ip1: can increase IO independently
  - To migrate an EBS volume across AZ
    - Take a snapshot
    - Restore the snapshot to another AZ
    - EBS backups use IP and you shouldn't run them while your applcation is handling a lot of traffic
  - Root EBS Volumes of instances get terminated by default if the EC2 instance gets terminated. (you can disable that)
- EBS vs EFS - Elastic File System
  ![alt text](image-17.png)
  - Mounting 100s of instances across AZ
  - EFS share website files (WordPress)
  - Only for Linux Instances (POSIX)
  - EFS has a higher price point than EBS
  - Can leverage EFS-1A for cost savings
  - Remember: EFS vs EBS vs Instance Store
- EBS vs EFS - Cleanup


## Scalability & High Availability
- Scalability & High Availability
  - Scalability means that an application / system can handle greater loads by adapting
  - There are two kinds of scalability
    - Vertical Scalability
    - Horizontal Scalability (-elasticity)
  - Scalability is linked byt different to High Availability
  - Let's deep dive into the distinction, using a call center as an example
- Vertical Scalability
  - Vertically scalability means increasing the size of the instance
  - For example, your applcations runs on a t2.micro
  - Scaling that application vertically means running it on a t2.large
  - Vertical scalability is very common for non-distributed systems, such as a database
  - RDS, ElaticCache are services that can scale vertically
  - There's usually a limit to how much you can vertically scale (hardware limit)
- Horizontal Scalibility
  - Horizontal Scalability means increasing the number of instances / systems for your applcations
  - Horizontal scaling implies distributed systems
  - This is very common for web applications / modern applcations
  - It's easy to horizontally scale thanks the cloud offerings such as Amazon EC2
- High Avaliability
  - High Availability usually goes hand in hand with horizontal scaling
  - High Availability means running your application / system in at least 2 data center (==AZ)
  - The goal of HA is to survive a data center loss
  - The HA can be passive (for RDS Multi AZ for example)
  - The HA can be active (for horizontal scaling)
- High Avaliability & Scaliability For EC2
  - Verical Scaling: Increasing instance size (=scale up/down)
    - From: t2.nano - 0.5G of RAM, 1 vCPU
    - To: u-12tbl.metal - 12.3 TB of RAM, 448 vCPUs
  - Horizontal Scaling: Increase number of instances (=scale out/in)
    - Auto Scaling Group
    - Load Balancer
  - High availability: Run instances for the same application across multi AZ
    - Auto Scaling Group multi AZ
    - Load Balancer multi AZ

## Load Balancing
- What is load balacing
  - Load Blanaces are servers that forward traffice to multiple servers (e.g. EC2 instances) downstream
  ![alt text](image-18.png)

- Why use a load balancer
  - Spread load across multiple downstream instances
  - Expose a single point of access (DNS) to your application
  - Seamlessly handle failures of downstream instances
  - Do regular health checks to your instances
  - Provide SSL termination (HTTPS) for your websites
  - Enforce stickiness with cookie
  - High availability across zones
  - Separate public traffic from private traffic

- Why use an Elastic Load Balancer
  - An Elastic Load Balancer is a managed load balancer
    - AWS guarantees that it will be working
    - AWS takes care of upgrades, maintenance, high availability
    - AWS provides only a few configuration knobs
  - It costs less to setup your own load balancer but it will be a lot more effort on your end
  - It is integrated with many AWS offerings / services
    - EC2, EC2 Auto Scaling Groups, Amazon ECS
    - AWS Certificate Manager (ACM), CloudWatch
    - Route 53, AWS WAF, AWS Global Accelerator

- Health Checks
  - Health Checks are crucial for Load Balancers
  - They enable the load balancer to know if instances it forwards traffice to are available to reply to requests
  - The health check is done on a port and a route (/health is common)
  - If the response is not 200 (OK), then the isntance is unhealthy
  ![alt text](image-19.png)

- Types of load balanced on AWS
  - AWS has 4 kinds of managed Load Balancers
    - Classic Load Balancer (v1 - old generation) - 2009 - CLB
      - HTTP, HTTPS, TCP, SSL (secure TCP)
    - Application Load Balancer  (v2 - new generation) - 2016 - ALB
      - HTTPS, HTTPS, WebSocket
    - Network Load Balancer - 2017 - NLB
      - TCP, TLS (secure TCP), UDP
    - Gateway Load Balancer - 2020 - GWLB
      - Operates at layer 3 (Network layer) - IP Protocol
  - Overall, it is recommended to use the newer generation load balancers as they provide more features
  - Some load balancers can be setup as internal (private) and external (public) ELBs

- Load Balancer Security Groups
  ![alt text](image-20.png)

### Classic Load Balancer
- Classic Load Balancers (v1)
  - Supports TCP (Layer 4), HTTP & HTTPS (Layer 7)
  - Health checks are TCP or HTTP based
  - Fixed hostname
    $name.regioin.elb.amazonaws.com
  ![alt text](image-21.png)

- Classic Load Balancers Hands on
  - Create EC2 instance
  - Create a Classic Load Balancers
    - Configure assign security groups: HTTP
      - only from CLB
    - Configure health check
      ![alt text](image-22.png)
    - Add EC2 instances
      - 3 EC2 instance

### Application Load Balaner
- Application Load Balancer (v2)
  - Application load balancer is layer 7 (HTTP)
  - Load balancing to multiple HTTP applications across machines (target groups)
  - Load balancing to multiple applcations on the same machine (ex: containers)
  - Support for HTTP/s and WebSocket
  - Support redirects (from HTTP to HTTPS for example)
  - Routing tables to different target groups
    - Routing bases on path in URL
    - Routing based on hostname in URL
    - Routing based on Query String, Headers
  - ALB are a great fit for micro services & container-based applcation (example: Docker & Amazon ECS)
  - Has aport mapping feature to redirect to a dynamic port in EC2
  - In comparison, we'd need multiple Class Load Balancer per application
  ![alt text](image-23.png)

- Application Load Balancer (v2) - Target Groupss
  - EC2 instances (can be managed by an Auto Scaling Group)
  - ECS stasks (managed by ECS itself)
  - Lambda functions - HTTP request is translated into a JSON event
  - IP Addresses - must be private IPs
  - ALB can route to multiple target groups
  - Health checks are at the target group level

- Application Load Balancer (v2) - Query String/Parameter Routing
  ![alt text](image-24.png)

- Application Load Balancer (v2) - Good to know
  - Exied hostname (XX.region.elb.amazonaws.com)
  - The application servers don't see the IP of the client directly
    - The true IP of the client is inserted in the header X-Forwarded-For
    - We can also get Port (X-Forwarded-Port) and proto (X-Fowarded-Proto)
    ![alt text](image-25.png)

- Application Load Balancer (v2) - Hands on
  - Create Application Load Balancer
    - Internet-facing
    - Security Groups
    - Listeners and routing
      - target group: instances
        - 3 instances
        - Rules
          - Path
          - Request

### Network Load Balancer
- Network Load Balancer (v2)
  - Network load balancer (Layer 4) allow to
    - Forward TCP & UDP traffic to your instances
    - Handle millions of request per seconds
    - Less latency ~100ms (vs 400 ms for ALB)
  - NLB has one static IP per AZ, and supports assigning Elastic IP (helpful for whitelisting specific IP)
  - NLB are used for extreme performance TCP or UDP traffic
  - Not included in the AWS free tier
  ![alt text](image-26.png)

- Network Load Balancer (v2) - Target Group
  - EC2 Instances
  - IP Addresses - must be private IPs
  - Application Balancer
    ![alt text](image-27.png)

- Network Load Balanced (v2) - Hands on
  - Create Network Load Balancer
    - Internet-facing
    - Listeners and routing
      - TCP 80: Taget Group
  - Create a Target Group


### Gateway Load Balancer
- Gateway Load Balancer
  - Deploy scale and manage a fleet of 3rd party network virtual applianaces in AWS
  - Example: Firewalls, intrusion Detection and Prvention Systems, Deep Packet Inspection System, payload manipulation...
  ![alt text](image-28.png)
  - Operates at Layer 3 (Network Layer) - IP Packets
  - Combines the following functions:
    - Transparent Network Gateway - single entry/exit for all traffic
    - Load Balancer - distriubtes traffic to your virtual appliances
  - Uses the GENEVE protocol on port 6081
- Gateway Load Balancer - Target Groups
  - EC2 instances
  - IP Addresses - must be private IPs
  ![alt text](image-29.png)


### Sticky Sessions (Session Affinity)
- Sticky Sessions (Session Affinity)
  - It is possible to implement stickiness so that the same client is always redirected to the same instance behind a load balancer
  - This works for Class Load Balancers & Application Load Balancers
  - The "cookie" used for stickiness has an expiation date you control
  - Use case: make sure the use doesn't lose hias session data
  - Enabling stickiness may bring inbalance to the load over the backend EC2 instances
  ![alt text](image-30.png)

- Sticky Sessions - Cookie Names
  - Application-based Cookies
    - Custom cookie
      - Generated by the target
      - Can include any custom attriubtes required by the application
      - Cookie name must be specified individually for each target grouo
      - Don't use AWSLAB, AWSALBAPP, or AWSALBTG (reserved for use by the ELB)
    - Application cookie
      - Generated by the load balancer
      - Cookie name is AWSALBAPP
  - Duration-based Cookies
    - Cookie generated by the load balancer
    - Cookie name is AWSALB for ALB, AWSELB for CLB

- Cross-Zone Load Balancing
  ![alt text](image-31.png)
  - Appliation Load Balancer
    - Always on (can't be disabled)
    - Not charges for inter AZ data
  - Network Load balancer
    - Disable by default
    - You pay charges ($) for inter AZ data if enabled
  - Classic Load balancer
    - Disable by default
    - No charges for inter AZ data if enabled
- Cross-Zone Load Balancing - Hands on

- SSL/TLS - Basics
  - An SSL Certificate allows traffice between your clients and your load balancer to be encrypted in transit (in-flight encryption)
  - SSL refers to Secure Socket Layer, used to encrypt connections
  - TLS refers to Transport Layer Security, which is a new version
  - Nowadays, TLS certificateds are mainly used, but people still refer as SSL
  - Public SSL certificates are issued by Certificate Authorities (CA)
  - Combodo, Symantec, GoDayy, GlobalSign, Digicert, Letsencrypt, etc...
  - SSL certificates have an expiration date(you set) and must be renewed

- Load Balancer - SSL Certificates
  ![alt text](image-32.png)
  - The load balancer uses an X.509 certificate (SSL/TLS server certificate)
  - You can manage certificates using ACM (AWS Certificate Manager)
  - You can create upload your own certificates alternatively
  - HTTPS listener
    - You must specify a default certificate
    - You can add an optinal list of certs to support multiple domains
    - Client can use SNI (Server Name Indication) to specify to hostname they reach
    - Ability to specify a security policy to support older versions of SSL/TLS (legacy clients)

- SSL - Server Name Indication
  - SNI solves the problem of loading multiple SSL certificates onto one web server (to serve multiple websites)
  - It's a "newer" protocol and requires the client to indicate the hostname of the target server in the initial SSL handshake
  - The server will then find the correct certificate, or return the default one

  - Note
    - Only works for AALB & NLB (newer generation), Cloudfront
    - Does not work for CKB (old gen)
  ![alt text](image-33.png)

- Elastic Load Balancers - SSL Certificates
  - Classic Load Balancer (v1)
    - Support only one SSL certificate
    - Must use multiple CLB for multiple hostname with mulple SSL certificates
  - Application Load Balancer (v2)
    - Supports multiple listeners with multiple SSL certificates
    - Uses Server Name Indication (SNI) to make it work
  - Network Load Balancer (v2)
    - Supports Multiple listeners with multiple SSL certificates
    - Uses Server Name Indication (SNI) to make it work
  - Hands on
    - Edit Listeners in CLB/ALB/NLB
      - Load Balancer Protocol: HTTPS (Secure HTTP)
      - Cypheer: Predefined Security Policy
      - Certificate: select or upload the certificate 

- Connection Draining
  ![alt text](image-34.png)
  - Feature naming
    - Connection Draining - for CLB
    - Deregistraion Delay - for ALB & NLB
  - Time to complete "in-flight requests" while the instance is de-registering or unhealthy
  - Stops sending new requests to the EC2 instance which is de-registering
  - Between 1 to 3600 seconds (default: 300 seconds)
  - Can be disabled (set value to 0)
  - Set to low value if your requests are short

## Auto Scaling Group
- What's an Auto Scaling Group
  - In real-life, the load on your websites and application can change
  - In the cloud, you can create and get rid of servers very quickly
  - The goal of an Auto Scaling Group (ASG) is to
    - Scale out (add EC2 instances) to match a increased load
    - Scale in (remove EC2 instances) to match a decreased load
    - Ensure we have a minimum and a maximum number of machines running
    - Automatically Register new instances to a load balancer
- Auto Scaling Group in AWS
  - Minimum size
  - Acutual Size
  - Desired Capacity
  - Maximum size
  ![alt text](image-35.png)
- Auto Scaling Group in AWS - With Load Balancer
  ![alt text](image-37.png)
- ASGs have the following attributes
  - A launch configuration
    - AMI + Instance Type
    - EC2 User Data
    - EBS Volumes
    - Security Groups
    - SSH Key Pair
  - Min Size / Max Size / Initial Capacity
  - Network + Subnet info
  - Load Balancer info
  - Scaling policies
- Auto Scaling Alarms
  - It is possible to scale an ASG based on CloudWatch alarms
  - An Alarm monitors a metric (such as Average CPU)
  - Metrics are computed for the overall ASG instances
  - Base on the alarm
    - We can create scale-out policies (increase the number of instances)
    - We can create scale-in policies (decrease the number of instances)
  ![alt text](image-38.png)

- Auto Scaling New Rules
  - It is now possible to define "better" auto scaling rules that are directly managed by EC2
    - Target Average CPU Usage
    - Number of request on the ELB per instance
    - Average Network In
    - Average Nutwork Out
  - These rules are easier to set up and can make more sense
- Auto Scaling Custom Metric
  - We can auto scal based on a custom metric (ex: number of connected users)
    - Send custom metric from application on EC2 to CloudWatch (PutMetric API)
    - Create CloudWatch alarm to react to low/high values
    - Use the CloudWatch alarm as the scaling policy for ASG
- ASG Brain Dump
  - Scaling policies can be on CPU, Network... and can even be on custom metrics or based on a schedule (if you know your visitors patterns)
  - ASGs use Launch configurations or Launch Templates (newer)
  - To update an ASG, you must porivde a new launch configuration / launch template
  - IAM roles attached to an ASG will get assigned to EC2 instances
  - ASG are free. You pay for the underlying resources being launched
  - Having isntances under an ASG means that if they get terminated for whatever reason, the AS will automatically create new ones as a replacement Extra safety
  - ASG can terminate instances marked as unhealthy by an LB (and hence replace them)

- Auto Scaling Groups - Hands on
  - Create launch Template
    - AMI
    - Instance Tpye
  - Create an Auto Scaling Group
    - Instance purchase options:  Adhere to launch template
    - Load balancing
      - Attach to an existing load balancer target groups
      - Health checks:  ELB
    - Group Size
      - Desired capacity
      - Minimum capacity
      - Maximum capacity
    - Scaling policies: None

- Auto Scaling Groups - Dynamic Scaling Policies
  - Target Tracking Scaling
    - Most simple and easy to setup
    - Example: I want to the average AGG CPU to stay at around 40%
  - Simple / Step Scaling
    - When a CloudWatch alarm is triggered (example CPU > 70%) then add 2 units
    - When a CloudWatch alarm is triggered (example CPU < 30%) then add remote 1
  - Scheduled Actions
    - Anticipate a scaling based on known usage patterns
    - Example: increase the min capacity to 10 at 5 pm on Fridays
- Auto Scaling Groups - Predictive Scaling
  - Predictive scaling: continuously forecast load and schedule scaling ahead
    ![alt text](image-39.png)

- Good metrics to scale on
  - CPUUtilization: Average CPU
    - utilization across your instances
  - RequestContPerTarget
    - to make sure the number of requests per EC2 isntances is stable
    ![alt text](image-41.png)
  - Average Network In/Out (if you're application is network bound)
  - Any custom metric (that you push using CloudWatch)

- Auto Scaling Groups - Scaling Cooldowns
  - After a scaling activity happens, you are in the cooldown period (default 300 seconds)
  - During the cooldown periond, the ASG will not launch or terminate additional instances (to allow for metrics to stabilize)
  - Advice: Use a ready-to-use AMI to reduce configuration time in order to be serving request fasters and reduce the cooldown period
    ![alt text](image-42.png)

- Auto Scaling Groups - Scaling Policies Hands on
  - Setup Automatic scaling
    - Create scheduled action
    - Create Predictive scaling policies
      - Scale based on forecast
      ![alt text](image-43.png)
    - Create Dynamic scaling policies
      - Simple scaling
      ![alt text](image-44.png)
      - Step scaling
      ![alt text](image-45.png)
      - Target tracking scaling
      ![alt text](image-46.png)
  - Monitoring
  - Instance Management
  - Use stress
    ```
    stress -c 4
    ```
  - CloudWatch Alarms

- ASG for Solutions Architects
  - ASG Default Termination Policy (simplified version)
    1. Fine the AZ which has the most number of instances
    2. If there are multiple instances in the AZ the choose from, delete the one with the oldest launch configuration 
  - ASG tries the balance the number of instances across AZ by default
    ![alt text](image-47.png)

- ASG for Solutions Architects - Lifecycle Hooks
  - By default as soon as an instance is launched in an ASG it's in service
  - You have the ability to perform extra steps before the instance goes in service (Pending state)
  ![alt text](image-48.png)

- ASG for Solutions Architects - Launch Tempalte vs Launch Configuration
  - Both:
    - ID of the Amazon Machine Image (AMI), the instance type, a key pair, security groups, and the other parameters that you use to launch EC2 instances (tags, EC2 user-data...)
  - Launch Configuration (legacy)
    - Must be-created every time
  - Launch Template (newer)
    - Can have multiple versions
    - Create parameters subets (partial configuration for re-use inheritance)
    - Provision using both On-Demond and Spot instances (or a mix)
    - Can use T2 unlimited burst feature
    - Recommended by AWS going forward


## RDS

- AWS RDS Overview
  - RDS stands for Relational Database Service
  - It's a managed DB servce for DB use SQL as a query language
  - It allows you to create databases in thoe cloud that are managed by AWS
    - Postgres
    - MySQL
    - MariaDB
    - Oracle
    - Microsoft SQL Server
    - Aurora (AWS Proprietary database)

- Advantage over using RDS versus deploying DB on EC2
  - RDS is a managed service
    - Automated provsioing, OS patching
    - Continuous backups and restore to specific timestamp (Point in Time Restore)
    - Monitoring dashboard
    - Read replicas for improved read performance
    - Multi AZ setup for DR (Disaster Recovery)
    - Maintenance windows for upgrades
    - Scaling capability (vertical and horizontal)
    - Storage backend by EBS (gp1 or io1)
  - But yon can't SSH into your instances

- RDS Backups
  - Backups are  automatically enabled in RDS
  - Automated backups
    - Daily full backup of database (during the maintenance window)
    - Transaction logs are backed-up by RDS every 5 minutes
    - => ability to restore to any point in time (from oldest backup to 5 minutes ag0)
    - 7 days retention (can be increased to 35 days)
  - DB Snapshots
    - Manually triggered by the user
    - Retention of backup for as long as yor want

- RDS - Storage Auto Scaling
  - Helps you increase storage on your RDS DB instance dynamically
  - When RDS detects you are running out of free database storage, it scales automatically
  - Avoid manually scaling your database storage
  - You have to set Maximum Storage Threshold (maximum limit for DB storage)
  - Automatically modify storage if
    - Free storage is less than 10% of allocated storage
    - Low-storage lasts at least 5 minutes
    - 6 hours have passed since last modification
  - Useful for applcations with unpredictable workloads
  - Supports all RDS database engines (MariDB, MySQL, PortgreSQL, SQL Server, Oralce)

- RDS Read Replicas for read scalability
  - Up to 5 Read Replicas
  - With AZ, Cross AZ or Cross Region
  - Replication in ASYNC, so reads are eventually consistent
  - Replicas can be promoted to their own DB
  - Applications must update the connection string to leverage read replicas
  ![alt text](image-49.png)

- RDS Read Replicas - Use cases
  - You have production database that is taking on normal load
  - You want to run a reporting application to run some analytics
  - You create a Read Replica to run the new workload there
  - The production application is unaffected
  - Read replicas are used for SELECT (=read) only ony kind if statements (not INSERT, UPDATE, DELETE)
  ![alt text](image-50.png)

- RDS Read Replicas - Network Cost
  - In AWS there's a network cost when data goes from one AZ to another
  - For RDS Read Replicas within the same region, you don't pay that free
  ![alt text](image-51.png)

- RDS Multi AZ (Disaster Recovery)
  - SYNC replication
  - One DNS name - automatic app failover to standby
  - Increase availability
  - Failover in case of loss of AZ, loss of network, instance or storage failure
  - No manual intervention in apps
  - Not used for scaling
  - Note: The Read Replicas be setup as Multi AZ for Disater Recovery (DR)
  ![alt text](image-52.png)

- RDS - From Single-AZ to Multi-AZ
  - Zero downtime operation (no need to stop the DB)
  - Just click on 'modify' for the database
  - The following happens internally
    - A snapshot is taken
    - A new DB is restored from the snapshot in a new AZ
    - Synchronization is established between the two databases
  ![alt text](image-53.png)  

- RDS Hands on
  - Create database
    - Engine Tyep: MySQL
    - Templates: Free tier
    - DB instance identifier: saa-c03-database
    - Master username
    - Master password
    - Master Confrim password
    - DB instance size:  db.t2.micro
    - Allocated storage: 20 GiB
    - Enable storage autoscaling: disable
    - Publicly accessible: Yes
    - VPC security group
    - AZ
    - IAM db authentication: disable
    - Enable automatic backupsL: enable
    - Backup retention period: 7 days (7 ~ 35)
    - Backup windows: No preference
    - Enable deletion protection: disable
  - Update RDS instance
    - Instance actions > Create read replica    

  - Use `Sqlectron` connect to RDS

- RDS Security - Encrpytion
  - At rest encryption
    - Possibility to encrypt the master & read replicas with AWS KMS - AES-256 encryption
    - Encryption has to be defined at launch time
    - If the master is not encrypted, the read replicas cannot be encryped
    - Transparent Data Encryption (TDE) avaliable for Oracle and SQL Server
  - In-flight encryption
    - SSL certificates to encrypt data to RDS in flight
    - Provide SSL options with trust certificate when connecting to database
    - To enforce SSL
      - PostgreSQL: rds.force_ssl=1 in the AWS RDS Console (Parameter Groups)
      - MySQL: Within the DB
        GRANT USAGE ON *.* TO 'mysqluser'@'%' REQUIRE SSL;

- RDS Encryption Operations
  - Encrypting RDS backups
    - Snapshots of un-encrypted RDS databases are un-encrypted
    - Snapshots of encrypted RDS databases are encrypted
    - Can copy a snapshot into an encrypted one
  - To encrypt an un-encrypted RDS database
    1. Create a snapshot of the -n-encrypted database
    2. Copy the snapshot and enable encryption for the snapshot
    3. Restore the database from encrypted snapshot
    4. Migrate applcations to the new database, and delete the old database

- RDS Security - Network & IAM
  - Network Security
    - RDS databases are usually deployed within a private subnet, not in public one
    - RDS security works by leveraging security groups (the same conect as for EC2 instances) - it controls which IP/security group can cummunicate with RDS
  - Access Management
    - IAM policies help control who can manage AWS RDS (througt the RDS API)
    - Traditinal Username and Password can be used to login into the database
    - IAM-based authentication can be used to login into RDS MySQL & PostgreSQL

- RDS - IAM Authentication
  - IAM database authentication works with MySQL and PostgreSQL 
  - You don't need a password, just an authentication token obtained through IAM & RDS  API calls
  - Auth token has a lifetime of 15 minutes
  
  - Benefits
    - Network in/out must be encrypted using SSL
    - IAM to centrally message users instead of DB
    - Can leverage IAM Roles and EC2 instance profiles for easy integration

  ![alt text](image-54.png)

- RDS Secruity - Summary
  - Encryption at rest
    - Is done only when yoru first create the DB instance
    - or unencrypted DB => snaphot => copy snapshots as encrypted => create DB from snapshot
  - Your responsibility
    - Check the ports/IP/Security group inbound rules in DB's SG
    - In-database user creation and permissions or manage throught IAM
    - Creating a database with or without public access
    - Ensure the parameter groups or DB is configured  to only allow SSL connections
  - AWS responsibility
    - No SSH access
    - No manual DB patching
    - No manual OS patching
    - No way to audit the underlying instance


### Aurora

- Amazon Aurora
  - Aurora is a proprietary technology from AWS (not open sourced)
  - Postgres and MySQL are both supported as Aurora DB (that means your drivers will work as if Aurora was a Postgres or MySQL database)
  - Aurora is "AWS cloud optimized" and claims 6x performance improvement over MySQL on RDS, over 3x the performance of Postgres on RDS
  - Aurora storage automatically gross in increaments of 10GB, upt ot 128 TB
  - Aurora can have 15 replicas while MySQL has 5, and the replication process is faster (sub 10 ms replica lag)
  - Failover in Aurora is instantaneous. It's HA native.
  - Aurora costs more than RDS (20% more) -  but is more efficient

- Aurora High Availablity and Read Scaling
  - 6 copies of your data across 3 AZ
    - 4 copies out of 6 needed for writes
    - 3 copies out of 6 need for reads
    - Self healing with peer-to-peer replication
    - Storage is striped across 100s of volumes
  - One Aurora Instance takes writes (master)
  - Automated failover for master in less than 30 seconds
  - Master + uo to 15 Aurora Read Replicas serve reads
  - Support for Cross Region Replication
  ![alt text](image-55.png)

- Aurora DB Cluster
  ![alt text](image-56.png)

- Features of Aurora
  - Automatic fail-over
  - Backup and Recovery
  - Isolation and security
  - Industry compliance
  - Push-button scaling
  - Automated Patching with Zero Downtime
  - Advanced Monitoring
  - Routine Maintenance
  - Backtrack
    - restore data at any point of time without using backups

- Aurora Security
  - Similiar to RDS because used the same engines
  - Encryption at rest using KMS
  - Automated backups, snapshots and replicas are also encrypted
  - Encryption in flight using SSL (same process as MySQL or Postres)
  - Possibility to authenticate using IAM token (same method as RDS)
  - You are responsible for protecting the instance with securiry groups
  - You can't SSH

- Aurora Hands on
  - Create database
    - Engine options: Amazon Aurora
    - Edition: 
      - Amazon Aurora with MySQL compatiblity
      - Amazon Aurora with PostgreSQL compatiblity
    - Version: 5.6
    - Database Location: Regional
    - Database features
      - One writer and multiple reader
      - One writer and multiple reader - Parallel query
      - Multiple writers
      - Serverless
    - Templates
      - Production
      - Dev/Test
    - DB instance size
      - DB instancce class
        - Memory Optimized classes (r and x classes)
        - Burstable classes (t classes)
    - Avaliability & durability (Multi-AZ deployment)
      - Create an Aurora Replicat or Reader node in a different AZ
      - Don't create an Aurora Replica
    - Backup retention period: 1 to 35 days
    - Enable Encryption
      - Key in KMS
    - Backtrack
      - Enable backtrack
    - Maintenance
      - Enable auto minor version upgrade
  - Modify > Add Auto Scaling policy
    - Target 60%
    - Cluster capacity details
      - Minimum capacity: 1
      - Maximum capacity: 15

- Aurora Replicas - Auto Scaling
  ![alt text](image-57.png)

- Aurora - Custom Endpoints
  - Define a subset of Aurora Instances as a Custom Endpoint
  - Example: Run Analytical queries on specific replicas
  - The Reader Endpoint is generally not used after defining Custom Endpoints
  ![alt text](image-58.png)
  
- Aurora Serverless
  - Automated database instantiation and auto-scaling based on actiual usage
  - Good for infrequent, intermittent or unpredictable workloads
  - No capacity planning needed
  - Pay per second, can be more cost-effective
  ![alt text](image-59.png)

- Aurora Multi-Master
  - In case you want immediate failover for write node (HA)
  - Every node does R/W - vs promoting a RR as the new master

  ![alt text](image-60.png)

- Global Aurora
  - Aurora Cross Region Read Replicas
    - Useful for disaster recovery
    - Simple to put in place
  - Aurora Global Database (recommended)
    - 1 Primary Region (read/write)
    - Up to 5 secondary (read-only) regions, replication lag is less than 1 second
    - Up to 16 Read Replicas per secondary region
    - Helps for decreasing latency
    - Promoting another region (for disaster recovery) has an ROT of < 1 minute
  ![alt text](image-61.png)

- Aurora Machine Learning
  - Enables you to add ML-based predication to your applications via SQL
  - Simple, optimized and secure integration between Aurora and AWS ML services
  - Supported services
    - Amazon SageMaker (use with any ML model)
    - Amazon Comprehend (for sentiment analysis)
  - You don't need to have ML experence
  - Use cases: fraud detection, ads targeting, sentiment analysis, product recommendations
  ![alt text](image-62.png)


## Amazon ElastiCache

- Amazon ElatiCache Overview
  - The same way RDS is to get managed Relational Databases
  - ElastiCache is to get managed Redis or Memcached
  - Caches are in-memory databases with really high performance, low latency
  - Helps reduce load off of databases for read intensive workloads
  - Helps make your application stateless
  - AWS takes care of maintenance / patching, optimizations, setup, configuration, montoring, failure recovery and backups
  - Use ElastiCache involves heavy applicaton code changes

- ElastiCache Solution Architecture - DB Cache
  - Applications queries ElastiCache, if not available, get from RDS and store in ElastiCache
  - Help relieve load in RDS
  - Cache must have an invalidation strategy to make sure only the most current data is used in there
  ![alt text](image-63.png)

- ElastiCache Solution Architecture - Use Session Store
  - User logs into any of the application
  - The application writes the session data into ElastiCache
  - The user hits another instance of our application
  - The instance retrieves the data and the user is already logged in
  ![alt text](image-64.png)

- ElastiCache - Redis vs Memcached
  - REDIS
    - MultiAZ with Auto-Failover
    - Read Replicas to scale reads and have HA
    - Data Durability using AOF persistence
    - Backup and restore failure
  - MEMCACHED
    - Multi-node for partitioning of data (sharding)
    - No high availiable (replication)
    - No persistent
    - No backup and restore
    - Multi-threaded architecture
  ![alt text](image-65.png)

- ElastiCache Hand on
  - Create ElastiCache cluster
    - Cluster engine
      - Redis
      - Memcached
    - Node Type: cache.t2.micro
    - Number of replicas: 0
      - Will disable Muiti-AZ with Auto-Failover
    - Subnet group
    - Encryption with KMS
    - Enable automatic backups
    - Backup
      - Backup retention period: 1 ~ 7 days
      - Backup window
    - Maintenance
      - Maintenance windows
      - Topic for SNS notification
    - Advaned Redis settings
      - Subnet group
      - Preferred availability zone(s)
    - Security
      - Security groups
      - Encryption at-rest
      - Encryption in-transit
      - Redis AUTH

- ElastiCache -Cache Security
  - All caches in ElastiCache
    - Do not support IAM authentication
    - IAM policies on ElastiCache are only used for AWS API-level security
  - Redis AUTH
    - You can set a 'password/token' when you create a Redis cluster
    - This is an extra level of security for you cache (on top of security groups)
    - Support SSL in flight encryption
  - Memcached
    - Supports SASL-based authentication (advanced)
  ![alt text](image-66.png)

- Patterns for ElastiCache
  - Lazzy Loading: all the read data is cached, data can become stale in cache
  - Write Through: Adds or update data in the cache when written to a DB (no stale data)
  - Session Store: store temporary session data in a cache (using TTL features)
  ![alt text](image-67.png)

  - Quote: There are only tow hard things in Computer Science: cache invalidation and naming things

- ElastiCache - Redis Use Case
  - Gaming Leaderboards are computationally compex
  - Redis Sorted sets guarantee both uniqueness and element ordering
  - Each time a new element added, it's ranked in real itme, then added in correct order
  ![alt text](image-69.png)


## DNS

- Whats DNS
  - Domain Name System which translates the human friendly hostnames into the machine IP addresses
  - Dns is the backbone of the Internet
  - DNS uses hierarchical naming structure

- DNS Terminologies
  - Domain Registra: Amazon Route 53, GoDaddy...
  - DNS Records: A, AAAA, CNAME, NS,...
  - Zone File: Contains DNS records
  - Name Server: resolves DNS queries (Authoritative or Non-Authoritative)
  - Top Level Domain (TLD)L .com, .us, .in, .gov, .org...
  - Second Level Domain (SLD): amazon.com, google.com,...

- How DNS Works
  - A hight available, scalable, fully managed and Authoritative DNS
    - Authoritative = the customer (you) can update the DNS records
  - Route 53 is also a Domain Registra
  - Ability to check the health of your resources
  - The only AWS service which provides 100% availability SLA
  - Why route 53?  53 is a reference to the tranditional DNS port
  ![alt text](image-71.png)

## Route 53
- Route 53 - Records
  - How you want to route traffice for a domain
  - Each record contains
    - Domain/subdomain Name - e.q., example.com
    - RecordType - e.g.,A or AAAA
    - Value - e.g., 123.456.789.123
    - Routing Policy - how Route 53 responds to queries
    - TTL - amount of time the record cached at NDS Resolvers
  - Route 53 supports the following DNS record types
    - (must know) A/AAAA/CNAME/NS
    - (advanced) CAA/DS/MX/NAPTR/PTR/SOA/TXT/SPF/SRV

- Route 53 - Record Types
  - A - maps a hostname to IPv4
  - AAAA - maps a hostname to IPv6
  - CNAME - maps a hostnaem to another hostname
    - The target is a domain which must have an A or AAAA record
    - Can't create a CNAME record for the top node of a DNS namespace (Zone Apex)
    - Example: you can't create for example.com, but you can create for www.example.com
  - NS - Name Servers for the Hosted Zone
    - Control how traffic is routed for a domain

- Route 53 - Hosted Zones
  - A contaienr for records that define how to route traffice to a domain and its subdomains
  - Public Hosted Zones - contains records that specify how to route traffice on the Internet (public domain names)
    - application1.mypublicdomain.com
  - Private Hosted Zones - contains records that specify how you route traffice within one or more VPCs (private domain names)
    - application1.mypublicdomain.internal
  - You pay $0.50 per month per hosted zone

- Route 53 - Public vs. Private Hosted Zones
  ![alt text](image-73.png)

- Route 53 Hands on
  - Register Domain
    - Fill in the required fields in the form.
  - Hosted zone details
    - Record Type: NS
    - Record Type: SOA

- Route 53 create our first record
  - Record type: A
  - Test it with `dig` and `nslookup` command
    ```
    dig example.com

    nslookup example.com
    ```

- Route 53 EC2 setup
  - Create 3 EC2 instance in 3 regions
  - Create an Application Load Balancer
    - Add the 3 instance

- Route 53 - Records TTL (Time to Live)
  - High TTL - e.g., 24hr
    - Less traffice on Route 53
    - Possibly outdated records
  - Low TTL - e.g., 60 sec
    - More traffic on Rotue 53 ($$)
    - Records are outdated for less time
    - Easy to change records
  - Except for Alias records, TTL is mandatory for each DNS record
  ![alt text](image-74.png)

- Route 53 CNAME vs Alias
  - AWS Resources (Load Balancer, CloudFront...) expose an AWS hostname
    - lbl-1233.us-east-2.elb.amazonaws.com and you want myapp.mydomain.com
  - CNAME
    - Points a hostname to any other hostname. (app.mydomain.com => blabla.anything.com)
    - ONLY FOR NOT ROOT DOMAIN (aka. something.mydomain.com)
  - Alias
    - Points a hostname to an AWS Resource (app.mydomain.com => blabla.amazonaws.com)
    - Works for ROOT DOMAIN and NON ROOT DOMAIN (aka.mydomain.com)
    - Free of charge
    - Native health check

- Route 53 - Alias Records
  - Maps a hostname to an AWS resource
  - An extension to DNS functionality
  - Automatically recognizes changes in the resources' IP addresses
  - Unlik CNAME, it can be used for the top node of a DNS namespace (Zone Apex), e.g.: example.com
  - Alias Record is always of type A/AAAA for AWS resources (IPv4/IPv6)
  - You can't set the TTL
  ![alt text](image-75.png)

- Route 53 - Alias Records Targets
  - Elastic Load Balancers
  - CloudFront Distributions
  - API Gateway
  - Elastic Beanstalk environments
  - S3 Websites
  - VPC Interface Endpoints
  - Global Accelerator
  - Route 53 record in the same hosted zone

  - You cannot set an ALIAS record for an EC2 DNS name

- Route 53 - Routing Policies
  - Define how Route 53 responds to DNS queries
  - Don't get confused by the word 'Routing'
    - It's not the same as Load balancer routing which routes the traffice
    - DNS does not route any traffice, it only responds to the DNS queries
  - Route 53 supports the following Routing Poilcies
    - Simple
    - Weighted
    - Failover
    - Latency based
    - Geolocation
    - Multi-Value Answer
    - Geoproximity (using Route 53 Traffice Flow feature)

- Routing Policies - Simple
  - Typically, route traffice to a simple resource
  - Can spcify multiple values in the same record
  - If multiple values are returned, a random one is chosen by the client
  - When Alias enabled, specify only one AWS resource
  - Can't be associated with Health Checks
  ![alt text](image-76.png)

- Routing Policies - Weighted
  - Control the % of the requests that go to each specific resource
  - Aasign each record a relative weight
    - traffice (%) = Weight for a specific record / Sum of all the weights for all records
    - Weights don't need to sum up to 100
  - DNS records must have the same name and type
  - Can be assocated with Health Checks
  - Use cases: load balancing between regions, testing new application versions...
  - Assign a weight of 0 to a record to stop sending traffice to a resource
  - If all records have weight of 0, then all records will be returned equally
  ![alt text](image-77.png)

- Routing Policies - Latency-based
  - Redirect to the resource that has the least latency close to us
  - Super helpfull when latency for user is a priority
  - Latency is based on traffice between users and AWS Regions
  - Germany users may be directed to the US (if that's the lowest latency)
  - Can be associated with Health Checks (has a failover capability)
  ![alt text](image-78.png)

- Route 53 - Health Checks
  - HTTP Health Checks are only for public
  - Health Check => Automated DNS Failover
    1. Health checks that monitor an endpoint (application, server, other AWS resource)
    2. Health checks that montior other health checks (Calculated Health Checks)
    3. Health checks that montior CloudWatch Alarms (full controll!!) - e.g. throttles of DynamoDB, alarms on RDS, custom metrics, ...(helpfull for private resources)
  - Health Checks are integrated with CS metrics
  ![alt text](image-79.png)

- Health Checks - Monitor an Endpoint
  - About 15 global health checkers will check the endpoint health
    - Healthy/Unhealthy Threshold - 3 (default)
    - Interval - 30 sec (can set to 10 sec - higher cost)
    - Supported protocol: HTTP, HTTPS and TCP
    - if > 18% of health checkers report the endpoint is healthy, Route 53 considers is Healthy. Otherwise, it's Unhealthy
    - Ability to choose which locations you want Route 53 to use
  - Health Checks pass only when the endpoint responds with the 2xx and 3xx status codes
  - Health Checks can be setup to pass/fail based on the text in the first 5120 bytes of the response
  - Configure you router/firewall to allow incoming requests from Route 53 Health Checkers
  ![alt text](image-80.png)

- Route 53 - Calculated Health Checks
  - Combine the results of multiple Health Checks into a single Health Check
  - You can use OR, AND, or NOT
  - Can monitor up to 256 Child Health Checks
  - Specify how many of the health checks need to pass to make the parent pass
  - Usage: perform maintenance to your website without cauing all health checks to fail
  ![alt text](image-81.png)

- Health Checks - Private Hosted Zones
  - Route 53 health checkers are outside the VPC
  - They can't access private endpoints (private VPC or on-premises resource)

  - You can create a CloudWatch Metric and associate a CloudWatch Alart, then create a Health Check that the alarm itself

  ![alt text](image-82.png)

- Route 53 Hands on
  - Route 53 > Create health check
    - Want to monitor
      - Endpoint
      - Status of other checks (calculated health check)
      - Status sof CloudWatch alarm
    
    - Endpoint
      - Endpoint
        - Protocol
        - IP Address
        - Host name
        - Port
        - Path
      - Advanced
        - Request interval
        - Failure threshold
        - String matching
        - Latency graphs
        - Invert health check status
        - Disable health check
        - Health checker regions
          - Customize
          - Use recommended
      - Get notified when health check fails
        - Create alarm
    - Route 53 > Health checks
      - See Status in the list
        - Health checkers
    - EC2 instance
      - Security Group
        - Allow inbound

    - Status of other checks (calculated health check)
      - Health checks to monitor
      - Report healthy when
        - at least \# of 3 selected health checks are healthy
        - all health checks are healthy (AND)
        - on ore more health checks are healthy (OR)
      - Invert health checks status
      - Disable health check

    - Status sof CloudWatch alarm
      - CloudWathc region
      - CloudWatch alarm
      - Health check status
        - the status is healthy
        - the status is unhealthy
        - use last known status

### Routing Policies - Failover (Active-Passive)

- Routing Policies - Failover (Active-Passive)
  ![alt text](image-83.png)
- Hands on
  - Create record
    - Routing policy: Failover
    - Failover record type
      - Primary
      - Secondary
    - Health check

### Routing Policies - Geolocation

- Routing Policies - Geolocation
  - Different from Latency-based
  - This routing is based on use location
  - Specify location by Continent, Country or by US State (if there's overlapping, most precise location selected)
  - Should create a 'Default' record (in case there's no mwatch on location)
  - Use cases: website localization, restrict content distribution, load balancing,...
  - Can be associated with Health Checks
  ![alt text](image-84.png)
- Hands on
  - Create record
    - Routing policy: Geolocation
    - Location

### Routing Policies - Geoproximity

- Routing Policies - Geoproximity
  - Route traffice to your resources based on the geographic location of users and resources
  - Ability to shift more traffice to resources based on the defined bias
  - To change the size of the geographic region, specify bias values
  ![alt text](image-85.png)
    - To expand (1 to 99) - more traffice to the resource
    - The shrink (-1 to -99) - less traffice to the resource
  - Resources can be
    - AWS resources (specify AWS region)
    - Non-AWS resources (specify Latitude and Longitude)
  - You must use Route 53 traffic Flow (advanced) to use this feature

- Route 53 - Traffice Flow
  - Simplify the process of creating and maintaining records in large and complex configurations
  - Visual editor to manage compex routing decision trees
  - Configurations can be saved as Traffice Flow Policy
    - Can be applied to different Rotue 53 Hosted Zones (different domain names)
    - Support versioning
  ![alt text](image-86.png)
  - Hands on
    - Create Traffic Policy
      - DNS Type
        - A
        - AAAA
        - CNAME
        - MX
        - PTR
        - SPF
        - SRV
        - TXT
      - Connect To...
        - Weighted rule
          - Weight
        - Failover rule
          - Primary
          - Secondary
        - Geolocation rule
        - Latency rule
        - Multivalue answer rule
        - Geoproximity rule
          - Endpoint Location
          - Bias: -99 ~ 99
          ![alt text](image-87.png)
        - New endpoint
          - DNS Type
    - Create policy records with traffice policy
      - Policy records
        - $50 per month
      ![alt text](image-88.png)


### Routing Policies - Multi-Value

- Routing Policies - Multi-Value
  - Use when routing traffice to multiple resources
  - Route 53 return nultiple values/resources
  - Can be associated with Health Checks (return only values from healthy resources)
  - Up to 8 healthy records are returned for each Multi-Value query
  - Multi-Value is not a substitute for having an ELB
  ![alt text](image-89.png)

## 3rd Party Domains & Route 53

- Domain Registar vs DNS Service
  - You buy or register your domain name with Domain Registrar typically by paying annual charges (e.g., GoDaddy, Amazon Registrar Inc,...)
  - The Domain Registrar usually provides you with a DNS service to manage yhour DNS records
  - But you can use another DNS service to manage your DNS records
  - Example: purchase the domain from GoDaddy and use Route 53 to maange your DNS records
  ![alt text](image-90.png)

- GoDaddy as Registrar & Route 53 as DNS service
  ![alt text](image-91.png)

- 3rd Party Registrar with Amazon Route 53
  - If you buy your domain on a 3rd party registrar, you can still use Route 53 as the DNS service provider
    1. Create a Hosted Zone in Route 53
    2. Update NS Records on 3rd party website to use Route 53 Name Servers
  - Domain Registrar != DNS Service
  - But every Domain Registrar usually comes with some DNS fatures

- Route 53 - Cleanup
  - EC2 instance
  - ELB
  - Target Groups

## Solution Architecture Disussion

### Introduction
- Introduction
  - These solutions architectures are the best part of this course
  - Lets understand how all the technologies we've seen work together
  - This is a section you need to be 100% comfortable with
  - We'll see the progression of a Solution's architect mindset through many sample case studies
    - WhatIsTheTime.com
    - MyClothese.com
    - MyWordPress.com
    - Instantiating applications quickly
    - Beanstalk


### Stateless Web App: WhatIsTheTime.com

- Feature
  - It allows poeple to know what time it is
  - We don't need a database
  - We want to start small and can accept downtime
  - We want to fully scale vertically and horizontally, no downtime
  - Let's go through the Solutions Arahitect journey for this app

![alt text](image-93.png)

- In this lecture we've discussed
  - Public vs Pirvate IP and instances
  - Elastic IP vs Route 53 vs Load Balancers
  - Rotue 53 TTL, A records and Alias Records
  - Maintaining EC2 instances manually vs Auto Scaling Groups
  - Multi AZ to survive disasters
  - ELB Health Checks
  - Security Group Rules
  - Reservation of capacity for costing savings when possible
  - We're considering 5 pillars for a well architecuted applcation: cost, performance, reliability, security, oerationally excellence


### Statefull Web App: MyClothes.com
- Feature
  - MyClothes.com allows people to buy clothese online
  - There's shopping cart
  - Our website is having hundreds of users at the same time
  - We need to scale, maintain horizontal scalability and keep our web application as stateless as possbile
  - Users should not lose their shopping cart
  - Users should have their details (address, etc) in a database
  ![alt text](image-94.png)

- Introduce Server Session
  - Stateless HTTP requests are heavier
  - Security risk (cookie can be latered)
  - Cookie must be validated
  - Cookie must be less than 4 4KB
  ![alt text](image-95.png)

- Storing User Data in a database
  ![alt text](image-96.png)

- Multi AZ - Servive disasters
  ![alt text](image-97.png)

- 3-tier architectures for web applications
  - ELB sticky sessions
  - Web clients for storing cookies and making our web app stateless
  - ElastiCache
    - For storing sessions (alternative: DynamoDB)
    - For caching data from RDS
    - Muiti AZ
  - RDS
    - For stroing user data
    - Read replicas for scaling reads
    - Multi AZ for disaster recovery
  - Tight Security with security groups referencing each other

### Statefull Web App: MyWordPress.com

- Features
  - We are trying to create a fully scalable WordPress website
  - We want to website to access and corectly display picture uploads
  - Our user data, and the blog content should be stored in a MySQL database

- RDS layer
  ![alt text](image-98.png)
- Scaling with Aurora: Multi AZ & REad Replicas
  ![alt text](image-99.png)
- Storing images with EBS
  ![alt text](image-100.png)
- Storing images with EFS
  ![alt text](image-92.png)


### In this lecture we've disussed

- Aurora Database to have easy Multi-AZ and Read-Replicas
- Storing data in EBS (single instance application)
- Vs Storing data in EFS (distributed application)

## Instantiating Applications quickly

- EC2 Instances
  - Use a Golden AMI: Install your applications, OS dependencies etc.. beforehand and launch your EC2 instance from the Golden AMI
  - Bootstrap using user Data: For dynamic configuration, use User Data scripts
  - Hybrid: mix Golden AMI and User Data (Elastic Beanstalk)
- RDS Databases
  - Restore from a snapshot: the database will have schemas and data ready
- EBS Volumes
  - Restore from a snapshot: the disk will already be formatted and have data

### Elastic Beanstalk

- Typical architecture: Web App 3-tier
  ![alt text](image-101.png)


- Developer problems on AWS
  - Managing infrastructure
  - Deploying Code
  - Congiuring all the dababases, load balancers, etc
  - Scaling concerns
  - Most web apps have the same architecture (ALB + ASG)
  - All the developers want is for their code to run
  - Possibly, consistently across different applications and environments

- Elastic Beanstalk - Overview
  - Elastic Beanstalk is developer centric view of deploying an application on AWS
  - It uses all the component's we've seen before: EC2, ASG, ELB, RDS,...
  - Managed server
    - Automatically handles capacity provisioning, load balancing, scaling, application health monitoing, instance configuration,...
    - Just the application code is the responsiblity of the developer
  - We still have full control over the configuration
  - Beanstalk is free but you pay for the underlying instances

- Elastic Beanstalk - Components
  - Application: collectioin of Elastic Beanstalk components (environments, versions, configurations,...)
  - Application Version: an iteration of your application code
  - Environment
    - Collection of AWS resources running an application version (only one application version at a time)
    - Tiers: Web Server Environment Tier & Worker Environment Tier
    - You can create multiple environment (dev, test, prod,...)
    ![alt text](image-102.png)

- Elastic Beanstalk - Supported Platform
  - Go
  - Java SE
  - Java with Tomcat
  - .NET Core on Linux
  - .nET on Windows Server
  - Node.js
  - PHP
  - Python
  - Ruby
  - Packer Builder
  - Single Container Docker
  - Multi-container Docker
  - Preconfigured Docker
  - If not supported, you can write your custom platform (advanced)

- Web Server Tier vs. Worker Tier
  ![alt text](image-103.png)


- Elastic Beanstalk Hands on
  - Create Application
    - Platform
      - Node.js
    - Application code
      - Sample application
      - Upload your code
    - Presets
      - Single instances (free Tier eligible)
      - Sinle instance(using Spot instance)
      - High availability
      - High availability(using Spot and On-Demand instances)
      - Custom configuration


## Amazon S3

- Introduction
  - Amazon S3 is one of the main building blocks of AWS
  - It's advertised as "infinitely scaling" storage
  - It's widely popular and deserves its own section

  - Many websites use Amazon S3 as a backbone
  - Many AWS services uses Amazon S3 as an integration as well


- Amazon S3 Overvew - Buckets
  - Amazon S3 allows people to store objects (files) in "buckets" (directories)
  - Buckets must have a globally unique name
  - Buckets are defined at the region level
  - Naming convention
    - No uppercase
    - No underscore
    - 3-63 characters long
    - Not an IP
    - Must start with lowercase letter or number

- Amazon S3 Overvew - Objects
  - Objects (files) have a Key
  - The key is the FULL path
    - s3://my-bucket/my_file.txt
    - s3://my-bucket/my_folder/another_filder/my_file.txt
  - The key is composed of prefix + object name
    - s3://my-bucket/my_folder/another_name/my_file.txt
  - There's no conecpt of "directories" within buckets (although the UI will trick you to think otherwise)
  - Just keys with very long names that contain slashes ('/')

- Amazon S3 Overvew - Objects (continued)
  - Object values are the content of the body
    - Max Object Size is 5TB (5000GB)
    - If uploading more than 5GB, must use "multi-part upload"
  - Metadata (list of text key/value pairs - system or use metadata)
  - Tags (Unicode key/value pair - up to 10) - usefull for security / lifecycle
  - Version ID (if versioning is enabled)

- S3 Bucket Hands on
  - Create bucket
    - Region: eu-west-1
    - Block all public access
    - Bucket Versioning: Disable
  - Upload file
    - Add files
    - Object actions > Open (Presigned URL)
      ![alt text](image-116.png)
    - Object URL
  - Create folder
    - Add files
  - Delete objects

- S3 Versioning
  - You can version your files in Amazon S3
  - It is enabled at the bucket level
  - Same key overwrite will increment the "version": 1,2,3...
  - It is best practice to version your buckets
    - Protect against unintended deletes (ability to restore a version)
    - Easy roll back to previous version
  - Notes
    - Any file that is not versioned prior to enabling versioning will have version "null"
    - Suspending versioning does not delete the previous versions

- S3 Versioning Hands on
  - Bucket > Properties
    - Bucket Versioning: Enable
  - List versions
  - Delete objects
    - Type: Delte marker
    ![alt text](image-117.png)
  - Retore an object
    - Delete the delete marker

- S3 Encryption for Ojbects
  - There are 4 methods of encrypting object in S3
    - SSE-S3: encrypt S3 object using keyss handled & managed by AWS
    - SSE-KMS: leverage AWS Key Management Service to manage encryption keys
    - SSE-C: when you want to manage yor own encryption keys
    - Client Side Encryption
  - It's important to understand which ones are adapted to which situation for the exam

- SSE-S3
  - SSE-S3: encrption using keys handled & maanged by Amazon S3
  - Object is encrypted server side
  - AES-256 encrption type
  - Must set header: "x-amz-server-side-encrption": "ASE256"
  ![alt text](image-118.png)
    
- SSE-KMS
  ![alt text](image-119.png)
  - SSE-KMS: encryption using keys handled & managed by KMS
  - KMS Advantages: user control + audit trail
  - Object is encrypted server side
  - Must set header: "x-amz-server-side-encryption":"aws:kms"

- SSE-C
  ![alt text](image-120.png)
  - SSE-C: server-side encryption using data keys fully maanged by the customer outside of AWS
  - Amazon S3 does not store the encrption key you provide
  - HTTPS must be used
  - Encrytion key must provided in HTTP headers, for every HTTP request mode

- Client Side Encryption
  ![alt text](image-121.png)
  - Client library such as the Amazon S3 Encryption Client
  - Client must encrypt data themselves before sending to S3
  - Client must decrypt data themselves before retrieving S3
  - Customer fully manages the kys and encryption cycle

- Encryption in transit (SSL/TLS)
  - Amazon S3 exposes
    - HTTP endpoint: non encrypted
    - HTTPS endpoint: encryption in flight
  - You're free to use the endpoint you want, but HTTPS is recommended
  - Most clients would use the HTTPS endpoint by default

  - HTTPS is mandatory for SSE-C
  - Encryption in flight is also called SSL/TLS

- S3 Encryption - Hands on
  - Server-side encryption settings
    - Server-side encryption: Enable
    - Encryption key type
      - Amazon S3 key (SSE-S3)
      - AWS Key Management Service by key (SSE-KMS)
        - AWS KMS key
          - AWS managed key (aws/s3)
          - Cloose from you KMS master kerys
          - Enter KMS master by ARN

  - Bucket
    - Default encryption
      - Encryption key type
  - For a File
    - Encryption settings
      - Use defualt encryption bucket settings
      - Override defult encryption bucket settings
        - Encryption key type

- S3 Security
  - User based
    - IAM policies - which API calls should be allowed for a specific user from IAM console
  - Resource Based
    - Bucket Policies - bucket wide rules from the S3 console - allows cross account
    - Object Access Control List (ACL) - finer gran
    - Bucket Access Control List (ACL) - less common
  - Note: an IAM principal can access an S3 object if
    - the user IAM permissions allow it OR the resource policy ALLOWS it
    - AND there's no explicit DENY

- S3 Bucket Policies
  ![alt text](image-122.png)
  - JSON based policies
    - Resources: buckets and objects
    - Actions: Set of API to Allow or Deny
    - Effect: Allow/Deny
    - Principal: The account or user to apploy the policy to
  - Use S3 bucket for policy to
    - Grant public access to the bucket
    - Force objects to be encrypted at upload
    - Grant access to another account (Cross Account)

- Bucket settings for Block Public Access
  - Block public access to buckets and objects granted through
    - new access control lists (ACLs)
    - any access control lists (ACLs)
    - new public bucket or access point policies
  - Block public and cross-account access to buckets and objects through any public bucket or access point policies
  
  - These settings are created to prevent comapny data leaks
  - If you know your bucket should never be public, leave these on
  - Can be set at the account level

- S3 Security - Other
  - Networking
    - Supports VPC Endpoints (for instances in VPC without www internet)
  - Logging and Audit
    - S3 Access Logs can be stored in other S3 bucket
    - API calls can be logged in AWS CloudTrail
  - User Security
    - MFA Delete: MFA (multi factor authentication) can be required in versioned buckets to delete objects
    - Pre-Signed URLs: URLs that are valid only for a limited time (ex: premium video service for logged in users)

- S3 Bucket Policies - Hands on
  - Bucket policy
    - AWS Policy Generator
      - Step 1: Select Policy Type
        - Select Type of Policy: S3 Bucket Policy
      - Step 2: Add Statement(s)
        - Effect
          - Allow
          - Deny
        - Principal: *
        - AWS Service: Amazon S3
        - Actions: Put Object
        - ARN
      - Add Conditions  (Optional)
        - Condition: Null
        - Key: s3-x-amz-server-side-encryption
        - Value: true

      - Step 1: Select Policy Type
        - Select Type of Policy: S3 Bucket Policy
      - Step 2: Add Statement(s)
        - Effect
          - Allow
          - Deny
        - Principal: *
        - AWS Service: Amazon S3
        - Actions: Put Object
        - ARN: ${BUCKET_ARN}/*
      - Add Conditions  (Optional)
        - Condition: StringNotRequals
        - Key: s3-x-amz-server-side-encryption
        - Value: AES256

- S3 Websites
  - S3 Websites
    - S3 can host static websites and have accessible on the www
    - The website URL will be
      - <bucket-name>.s3-website-<AWS-region>.amazonaws.com
    - If you get a 403 (Forbidden) error, make sure the bucket policy allows public read!

  - Hands on
    - Upload index.html/error.html to the bucket
    - In the properties tab of the bucket
      - Edit static website hosting
        - Static website hosting: Enable
        - Hosting type
          - Host a static website
          - Redirect requests for an object
      - Index document: index.html
      - Error document: error.html

    - Permission
      - Block all public access: uncheck
      - Bucket policy
        - Select Type of Policy: S3 Bucket Policy
        - Effect: Allow
        - Principal: *
        - AWS Service: Amazon S3
        - Actions: Get Objects
        - ARN: <bucket-name>/*

- S3 CORS - Explained
  - An origin is a schema (protocol), host(domain) and port
    - E.g.: https://www.example.com (implied port is 443 for HTTPS, 80 for HTTP)
  - CORS means Corss-Origin Resource Sharing
  - Web Browser based mechanism to allow requests to other origins while visiting the main origin
  - Same origin: https://example.com/app1 & https://example.com/app2
  - Different origin: https://www.example.com & https://www.other.com
  - The requests won't be fulfilled unless the other origin allows for the requests, using CORS Headers (ex: Access-Control-Allow-Origin)

- S3 CORS - Diagram
  ![alt text](image-123.png)

- S3 CORS - Diagram
  - If a client does a cross-origin request on our S3 bucket, we need to enable the correct CORS headers
  - It's a popular exam question
  - You can allow for a specific origin or for * (all origins)
  ![alt text](image-124.png)

- S3 CORS - Hands on
  - In the same bucket
  - In the different buckets
    - Permission > CORS
      ```
      [
        {
          "AllowedHeaders": {

          },
          "AllowedMethods": {

          },
          "AllowedOrigins": {

          }
        }
      ]
      ```

- S3 Consistency Model
  - Strong consistency as of December 2020
  - After a:
    - successful write of a new object (new PUT)
    - or an overwrite or delete of an existing object (overwrite PUT or DELETE)
  - ...any:
    - subsequent read request immediately receives the latest verson of the object (read after write consistency)
    - subsequent list request immediately reflects changes (list consistency)
  - Available at no additional cost, without any performance impact

- IAM Roles and Policies - Hands on
  - Create policy
    ```
    {
      "Statement": {
        "Effect": "Allow",
        "Action": "s3:GetObject",
        "Resource": "arn:aws:s3:::<bucket-name>/*"
      }
    }
    ```
- AWS Policy Simulator
  - Users, Groups, and Roles
  - Policy Simualtor
    - Amazon S3
    - Action(s): PutObject

- S3 MFA-Delete
  - MFA (multi factor authentication) forces user to generate a code on a device (usually a mobile phone or hardware) before doing important operations on S3
  
  - To use MFA-Delete, enable Versioning on the S3 bucket
  - You will need MFA to
    - permanenetly delete an object version
    - suspend versioning on the bucket
  - You won't need MFA for
    - enabling versioning
    - listing deleted versons
  
  - Only the bucket owner (root account) can enable/disable MFA-Delete
  - MFA-Delete currently can only enabled using the CLI

- S3 MFA-Delete - Hands on
  - Edit Bucket Versioning
    - Bucket Versioning: Enable
    - MFA Delete
      ```
      aws s3api put-bucket-versioning --bucket <bucket-name> --versoning-configuration Status=Enabled,MFADelete=Enabled --mfa <mfa-device-arn>
      ```

- S3 Default Encryption vs bucket Policies
  - One way to "force encryption" is to use a bucket policy and refuse any API call to PUT an S3 object without encription headers
  ![alt text](image-125.png)
  - Another way is to use the "default encryption" option in S3
  - Note: Bucket Policies are evaluated before "default encryption"
  - Hands on
    - Bucket > Properties
      - Default encryption
        - Server-side encryption: Enable
        - Encryption key type: Amazon S3 key (SSE-S3)
    - Upload file
      - Server-side encryption settings
        - Server-side encryption
          - Do not specify an encryption key
          - Specify an encryption key
        - Encryption settings
          - Use default encryption bucket settings
          - Override default encryption bucket settings

- S3 Access Logs
  - For audit purpose, you may want to log all access to S3 buckets
  - Any request made to S3, from any account, authorized or denies, will be logged into another S3 bucket
  - That data can be analyzed using data analysis tools
  - Or Amazon Athena as we'll see later in this section

  - The log format is at
    https://doc.aws.amazon.com/AmazonS3/latest/dev/LogFormat.html

  ![alt text](image-126.png)

- S3 Access Logs: Warning
  - Do not set your logging bucket to be the monitored bucket
  - It will create a logging loop, and your bucket will grow in size exponentially
  ![alt text](image-127.png)

- S3 Access Logs - Hands on
  - Create bucket
    - Properties > Server access logging
      - Server access logging: Enable
      - Target bucket


- S3 Replicaton (CRR & SRR)
  - Must enable versioning in source and destination
  - Cross Region Replication (CRR)
  - Same Region Replicaton (SRR)
  - Bucket can be in different accounts
  - Copying is asynchronous
  - Must give proper IAM permission to S3

  - CRR - Use cases: compliance, lower latency access, replicaton across accounts
  - SRR - Use cases: log aggregation, live replication between production and test accounts
  ![alt text](image-128.png)

- S3 Replicaton - Notes
  - After activating, only new objects are replicated (not retroactive)
  - For DELETE operations
    - Can replicate delete markers from source to target (optinal setting)
    - Deleting with a version ID are not replicated (to avoid malicious deletes)
  - There is no "chaining" of replication 
    - If bucket 1 has replication into bucket 2, which has replication into bucket 3
    - Then objects created in bucket 1 are not replicated to bucket 3

- S3 Replication - Hands on
  - Bucket Versioning: Enable
  - Management > Replication Rule
    - Create role
      - Status: Enabled
      - Source bucket
        - Choose a rule scope
          - Limit the scope of this rule using one or more filters
          - This rule applies to all objects in the bucket
      - Destination
        - Choose a bucket in this account
        - Specify a bucket in another account
        - Bucket name
      - IAM role
      - Add replication options
        ![alt text](image-129.png)

- S3 pre-signed URLs
  - Can generate pre-signed URLs using SDK or CLI
    - For downloads (easy, can use the CLI)
    - For uploads (harder, must use the SDK)
  - Valid for a default of 3600 seconds, can change timeout with --expires-in[TIME_BY_SECONDS] argument
  - Users given a pre-signed URL inherit the permissions of the person who generated the URL for GET/PUT

  - Examples:
    - Allows only logged-in users to download a premium video on your S3 bucket
    - Allow an ever changing list of users to download files by generating URLs dynamically
    - Allow temporarily a user to upload a file to precise location in our bucket

- S3 pre-signed URLs - Hands on
  - CLI
    ```
    aws s3 presign s3://<bucket-name>/<object-name> --region eu-west-1 --expires-in 300

    # set the proper signature version in order not to get issues when generating URLs for encrypted files
    aws configure set default.s3.signature_version s3v4


### S3 Storage

- S3 Storage Classes
  - Amazon S3 Standard - General Purpose
  - Amazon S3 Standard-Infrequent Access (IA)
  - Amazon S3 One Zone-Infrequent Access
  - Amazon S3 Intelligent Tiering
  - Amazon Glacier
  - Amazon Glacier Deep Archive
  - Amazon S3 Reduced Redundancy Storage (deprecated -omitted)
    
  ![alt text](image-130.png)
  https://aws.amazon.com/s3/storage-classes/

- Amazon S3 Standard - General Purpose
  - High durability (99.999999999%) of objects across multiple AZ
  - If you store (10,000,000) objects with Amazon S3, you can on average expect to incur a loss of a simple object once every 10,000 years
  - 99.99% Availability over a given year
  - Sustain 2 concurrent facility failures
  - Use Cases: Big Data analytics, mobile & gaming applications, content distribution

- Amazon S3 Standard - Infrequent Access (IA)
  - Suitable for data that is less frequently accessed, but requires rapid access when needed
  - High durability (99.999999999%) of objects across multiple AZs
  - 99.9 Availability
  - Low ocst compared to Amazon S3 Stardard
  - Sustain 2 concurrent facility failures
  - Use Cases: As a data store for disaster recovery, backups...

- S3 One Zone - Infrequent Access (IA)
  - Same as IA but data is stored in a single AZ
  - High durability (99.999999999%) of objects in a single AZ; data lost when AZ is destroyed
  - 99.5 % Availability
  - Low Latency and high throughput performance
  - Supports SSL for data at transit and encryption at rest
  - Low ost compared to IA (by 20%)
  - Use Cases: Storing secondary backup copies of on-premise data, or storing data you can recreate

- S3 Intelligent Tiering
  - Same low latency and high thoughput performance of S3 Standard
  - Small monthly monitoring and auto-tiering free
  - Automatically moves objects between two access tiers based on chaning access patterns
  - Designed for durability of 99.999999999% of objects across multiple Availability Zones
  - Resilient againt events that impact an entire Availability Zone
  - Designed for 99.9 avaliability over a given year

- S3 Glacier
  - Low cost object storage meant for archiving / backup
  - Data is retained for the longer term (10s of years)
  - Alternative to on-premise magnetic tape storage
  - Average annual durability is 99.999999999%
  - Cost per storage per month ($0.004 / GB) + retrieval cost
  - Each item in Glacier is called "Archive" (up to 40TB)
  - Archives are stored in "Vaults"

- Amason Glacier & Glacier Deep Archive
  - Amason Glacier - 3 retrieval options
    - Expedited (1 to 5 minutes)
    - Standard (3 to 5 hours)
    - Bulk (5 to 12 hours)
    - Minimum storage duration of 90 days
  - Amazon Glacier Deep Archive - for long term storage - cheaper
    - Standard (12 hours)
    - Bulk (48 hours)
    - Minimum storage duration of 180 days

- S3 Storage Classes - Price Comparison
  ![alt text](image-131.png)

- S3 Storage Classes - Hands on
  - Create bucket
    - Upload
      - Storage class
        - Standard-IA
        - One Zone-IA
        - Reduced redundancy
        - Intelligent-Tiering
        - Glacier
        - Glacier Deep Archive
      
      - Initiate restore
        - Restore objects from Glacier
          - Retrieval tier
            - Bulck retrieval
            - Standard retrieval
            - Expedited retrieval

- S3 - Moving between storage classes
  ![alt text](image-132.png)
  - You can transition objects between storage classes
  - For infrequently accessed object, move them to STANDARD_IA
  - For archive objects you don't need in real-time, GLACIER or DEEP_ARCHIVE
  - Moving objects can be automated using a lifecycle configuration

- S3 Lifecycle Rules
  - Transition actions: It defines when objects sare transitioned to another storage class
    - Move objects to Standard IA class 60 days after creation
    - Move to Glacier for archiving after 6 months
  - Expiration actions: configure objects to expire (delete) after some time
    - Access log files can be set to delete after 365 days
    - Can be used to delete old versions of files (if versioning is enabled)
    - Can be used to delete incomplete multi-part uploads
  - Rules can be created for a certain prefix (ex - s3://mybucketmp3/*)
  - Rules can be created for certain objects tags (ex - Department: Finance)

- S3 Lifecycle Rules - Scenario 1
  - Your application on EC2 creates images thumbnails after profile photos are uploaded to Amazon S3. These thumbnails can be easily recreated and only need to be kept for 45 days. The source images should be able to be immediately retrieved for these 45 days, and afterwards, the user can wait up to 6 hours. How would your design this?
    - S3 source images can be on STANDARD, with a lifecycle configuration to transition them to GLACIER after 45 days
    - S3 thumbnails can be on ONEZONE_IA, with a lifecycle configuration to expire them (delete them) after 45 days

- S3 Lifecycle Rules - Scenario 2
  - A rule in your company states that your should be able to recover your deleted S3 objects immediately for 15 days, although this may happen rarely. After this time, and for up to 365 days, deleted objects should be recoverable within 48 hours
    - You need to enable S3 versioning in order to have object versions, so that "deleted objects" are in fact hidden by a "delete marker" and can be recovered
    - You can transition these "noncurrent versions" of the object to S3_IA
    - You can transition afterwards these "nocurrent versions" to DEEP_ARCHIVE

- S3 Lifecycle Rules - Hands on
  - Create lifecyle rule
    - Lifecyle rule actions
      - Transition current versions of objects between storage classes
      - Transition previous versions of objects between storage classes
      - Expires current versions of objects
        ![alt text](image-134.png)
      - Permanently delete previous versions of objects
      - Delete expired markers or incomplete multipart uploads

    - Transision current version of objects between storage classes
      ![alt text](image-133.png)

- S3 Analytics - Storage Class Analysis
  - You can setup S3 Analytics to help determine when to transition objects from Standard to Stardard_IA
  - Does not work for ONEZONE_IA or GLACIER
  - Report is updated daily
  - Takes about 24h to 48 hours to first start
  - Good first steop to put together Lifecycle Rules (or improve them)

- S3 - KMS Limitation
  - If you use SSE-KMS, you may be impacted by the KMS limits
  - When you upload, it calls the GenerateDayKey KMS API
  - When you download, it calls the Decrypt KMS API
  - Count towards the KMS quota per second (550, 10000, 30000 req/s based on region)
  - You can request a quota increase using the Service Quotas Console
  ![alt text](image-135.png)

- S3 Performance
  - Multi-Part upload
    - recommended for files > 100MB, must use for files > 5GB
    - Can help parallelize uploads (speed up transfers)
    ![alt text](image-136.png)
  - S3 Transfer Acceleration
    - Increase transfer speed by transferring file to an AWS edge location which will forward the data to the S3 bucket in the target region
    - Compatible with multi-part upload
    ![alt text](image-137.png)

- S3 Performance - S3 Byte-Range Fetches
  - Parallelize GETs by requesting specific byte ranges
  - Better resilience in case of failures

  - Can be used to speed up downloads
    ![alt text](image-138.png)
  - Can be used to retrieve only partial data (for example the head of a file)
    ![alt text](image-139.png)

- S3 Select & Glacier Select
  - Retrieve less data using SQL by performing server side filterring
  - Can filter by rows & columns (simple SQL statements)
  - Less network transfer, less CPU cost client-side
  ![alt text](image-140.png)

- S3 Event Notifications
  - S3:ObjectCreated, S3:ObjectRemoved, S3:ObjectRestore, S3:Replication
  - Object name filtering possible (*.jpg)
  - Use case: generate thumbnails of images uploaded to S3
  - Can create as manay "S3 events" as desired
  - S3 event notifications typically deliver events in seconds but can sometimgs take a minute or longer
  - If two writes are made to a single non-versioned object at the same time, it is possible that only a single event notification will be sent
  - If you want to ensure that an event notification is sent for every successful write, you ca enable versioning on your bucket
  ![alt text](image-142.png)

- S3 Event Notifications - Hands on
  - Create queue
    ```
      ...
      "Action": {
        "sqs:SendMessage"
      },
      "Resoruce": "<SQS ARN>"
      ...

    ```

  - Create bucket
    - Properties > Event notifications
      - Create event notification
        - Event types
          ![alt text](image-143.png)
          ![alt text](image-144.png)
        - Destination
          ![alt text](image-145.png)

- S3 - Requester pays
  - In general, bucket owners pay for all Amazon S3 storage and data transfer cosnts associated with their bucket
  - With Requester Pays buckets, the requester instead of the bucket owner pays ths cost of the request and the data download from the bucket
  - Helpful when you want to share large datasets with other accounts
  - The requester must be authenticated in AWS (cannot be anonymous)
  ![alt text](image-146.png)


- Amazon Athena
  - Serverless query service to perform analysis against S3 objects
  - Uses standard SQL language to query the files
  - Supports CSV, JSON, ORC, Avro, and Parquet (build on Presto)

  - Pricing: $5.00 per TB of data scanned
  - Use compressed or columnar data for cost-savings (less scan)

  - Use cases: Business intelligence / analytics / reporting, analysis & query VPC Flow Logs, ELB Logs, CloudTrail trails, etc...
  - Exam Tip: analysis data in S3 using serverless SQL, use Athena
  ![alt text](image-147.png)

- Athena - Hands on
  - Create S3 bucket
  - Query editor > Manage settings
  - 
  ```
  create databse s3_access_logs_db;
  create external table if not exists s3_access_logs_db.mybucket_logs ...

  ```

- Glacier Vault Lock
  - Adopt a WORM (Write Once Read Many) model
  - Lock the policy for future edits (can no loger be changed)
  - Helpful for compliance and data retention
  ![alt text](image-148.png)

- S3 Object Lock (versioning must be enabled)
  - Adopt a WORM (Write Once Read Many) model
  - Block an object version deletion for a specified amount of time
  - Object retention
    - Retention Period: specifies a fixed period
    - Legal Hold: same protection, no expiry date
  - Modes
    - Governance mode: users can't overwrite or delete an object version or alter its lock settings unless they have special permissions
    - Compliance mode: a pertected object version can't be overwritten or deleted by any user, including the root user in your AWS account. When an object is locked in compliance mode, its retention mode can't be changed, and its retention period can't be shortened.


## AWS CloudFront Overview

- AWS CloudFront
  - Content Delivery Network (CDN)
  - Inproves read performance, content is cached at the edge
  - 216 Point of Presence globally (edge locations)
  - DDoS protection, integration with Shield, AWS Web Application Firewall
  - Can expose external HTTPS and can talk to internal HTTPS backends
  ![alt text](image-149.png)

- CloudFron - Origins
  - S3 bucket
    - For distributing files and caching them at the edge
    - Enhanced security with CloudFront Origin Access Identity (OAI)
    - CloudFront can be used as an ingress (to upload files to S3)
  - Custom Orign (HTTP)
    - Application Load Balancer
    - EC2 instance
    - S3 website (must first enable the bucket as a static S3 website)
    - Any HTTP backend you want

- CloudFront at a high level
  ![alt text](image-150.png)

- CloudFront - S3 as an Origin
  ![alt text](image-151.png)  

- CloudFront - ALB or EC2 as an origin
  ![alt text](image-152.png)

- CloudFront Geo Restriction
  - You can restrict who can access your distribution
    - Whitelist
    - Blacklist
  - The "country" is determined using a 3rd party Geo-IP database
  - Use case: Copyright Laws to control access to content

- CloudFront vs S3 Cross region Replication
  - CloudFront
    - Global Edge network
    - Files are cached for a TTL (maybe a day)
    - Great for static content that must be available everywhere
  - S3 Cross Region Replication
    - Must be setup for each region you want replication to happe
    - Files are updated in near real-time
    - Read Only
    - Great for dynamic content that needs to be available at low-latency in few regions

- CloudFront with S3 - Hands on
  - Create bucket
  - Create distribution
    - Origin domain
      ![alt text](image-153.png)
    - S3 bucket access
      ![alt text](image-154.png)
