# Note

## IAM


## EC2

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
  Source:  0.0.0.0/0 anywhere
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


## Security Groups

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
- Locked down to a regin/VPC combination
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
- EC2 Dedicated Instacnes
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
  [](https://.../ec2sp/v1/spot/home?region=us-east-1)

- How to terminate Spot Instances
  ![alt text](image-3.png)

- Spot Fleets
  - Spot Fleets = set of spot Instances + (optional) On-Demond Instances
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
    - Onre ore more security groups
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


