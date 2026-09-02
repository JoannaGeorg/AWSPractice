# AWS

## Account Setup

#### Budget alerts

- Enabled Alerts in billing preferences.
- Created a budget for alerting if it is nearing the set cost.
- Use cost Expolerer to check the spending of the account.

#### IAM user/group

- Creating an IAM user group which is the way the user account gets permissions.
  - Permissions are set for the group.
  - Users that are added to the group inherit those permissions.
- Setting Admin access permission and created the group.
- Created a user in the Admin group.
- Signed into AWS using the IAM user.

#### Explore AWS Console

- Accessed CloudShell and run a few commands to test.
- AWS Global Infrastructure:
  - **Region:** They are seperate physical locations around the world.
  - **Availability Zone:** is composed of 1 or more physical data center.
  - **AWS Global Network:** It connects all the regions - managed by AWS on bandwidth and latency.
- AWS Shared Responisibility Model:
  - AWS takes reponsibility of the features and services that it provides, however, the users are responsible to use and manage it appropriatly, according to their needs.
- Pricing:
  - **Compute:** Charged for the amount of resources used and the duration of use.
  - **Storage:** Charged for the quantity of data stored/allocated.
  - **Outbound Data Transfer:** Charged for the amount of data transferred out from the service.

#### AWS Authentication and Access Control

- The root user automatically has full permisions and cannot be restricted.
- IAM groups are used to set policies and the users in them inherit them.
- MFA - Multi-Factor Authentication - Add a device which has an authentication app.

## AWS Compute and Storage Services

#### AWS Compute Services

- Uses a Hypervisor to allocate the specified resources for a Virtual Machine to run.
- EC2 Instances:
  - Metadata version:
    - **V1 and V2:** No token is needed to access the metadata.
    - **V2 only:** A token is required to access the metadata.
  - User Data:
    - Bash script that is run on the instance the first time it runs.
- Permissions to EC2 instances:
  - Access Keys:
    - AWS CLI is configured with access keys associated with the account.
      - They are saved in plaintext - not very secure.
  - IAM Roles:
    - They have policies assigned to them.
    - No credentials on the CLI - removes the security risk of access keys.
    - Users assume a role and gain the corresponding permissions.
- AWS Batch:
  - It is a fully managed service that runs and schedules the containerized batch processing jobs.
  - Automatically provisions the compute resources and optimizes the workload distribution based on quantiy and scale.
- Amazon LightSail:
  - Gives the abilty to run virtual servers in the cloud with a simpler interface to work without requiring a strong background in technology.
  - AKA Simple Cloud Server.
- Docker Containers and Microservices:
  - Separate from each other - botts up faster than a simple virtual machine.
- Amazon Elastic Container Service (ECS):
  - A Service in which Docker Containers can be run on AWS.
    - Launch a ECS cluster - a logical grouping of tasks or services.
    - Launch a task - a running Docker Container.
      - Comes from a task definition that defines what is to be run.
    - Deploy an ECS service if needed which is used to maintain desired counter tasks.

#### AWS Storage Services

- **Block Based Storage:** Essentially a hard drive. Hard Disk Drive (HDD) and Solid State Drive (SSD).
- **File Based Storage:** Has bee created on top of a block based storage system, shared accross the network.
- **Object Based Storage:** Uploads objects using http protocol. Objects refer to ay type of files and no heirarchy.
- Amazon EBS:
  - It consists of volumes connected to an instance in an availabity zone.
  - EBS volumes offer persistant storage - long-term data storage.
  - Snapshots, a point-in-time state of an instance, are used as backup for EBS volume.
    - Snapshots are stored in S3, away from the availability zone.
- Data Life Cycle Manager (DLM)
  - Normally, Snapshots are taken manually. The DLM automates the creation , retention, and deletion of EBS Snapshots and EBS-backed AMI's.
- Amazon EFS:
  - Elastic File System: A shared file system, instances can be connected to the EFS file systems from multiple availabilty zones.
    - Regional File System - has mount targets in multiple availabilty zones.
    - One Zone File System - has a mount target only in a single availabilty zones.
- Amazon S3 Storage Classes:
  - Durability - protection aginst data loss and corruption.
  - Availabilty - measurement of the amount of time the data is available.
  - Storage classes are designed for durability and availabilty at different levels.
    - The difference lies in sensitivity of data, number of availabilty zones, access frequency, and latency.
- S3 Bucket:
  - Bucket is a container in which objects are stored.
  - Global unique names.
  - Versioning, Replication, and Lifecycle Rules:
    - **Versioning:** keeps multiple variants of an object in the same bucket.
      - Used to preserve, retrieve, and restore every version of every object stored.
    - **Replication:**
      - *Cross-Region Replication:* S3 bucket in one region and another in another region.
      - *Same-Region Replication:* S3 buckets in the same region used for replication.
    - **Life Cycle Management:**
      - *Transition action* defines when an object transfers to another storage class.
      - *Expiration action* defined when objects expire - deleted by s3.
- Amazon FSx:
  - Offers fully managed third-party file systems.
    - Amazon FSx for Windows File Server for Windows-Based Applications.
    - Amazon FSx for Lustre for compute-intensive workloads.
- Amazon S3 Galcier:
  - Amazon S3 Glacier is a secure and durable service for low-cost data archiving and long-term backup.
  - Extremely low cost, only pay as needed.
  - Three classes:
    - *S3 Glacier Instant Retrieval:* Used for archiving data that is rarely accessed and requires miliseconds retrieval.
    - *S3 Glacier Flexible Retrieval:* Used for achives where portions of the data need to be retrieved in minutes.
    - *S3 Glacier Deep Archive:* Used for achiving data that rarely needs to be accessed.
  - **Object Lock:** Stores objects using a write-once-read-many (WORM) model - prevents the objects from being overwritten for a fixed time or indefinately.
  - **Glacier Vault Lock:** Also used to enforce WORM model and can apply a policy and lock the policy from future edits.
- AWS Storage Gateway:
  - It is a hybrid cloud storage service.
  - Access cloud storage form on-premise applications.
  - Enables access to proprietary object storage (S3) using standard protocols.
  - **File Gateway**: File-based storage system. 
  - **Volume Gateway:** Block-based storage system.
  - **Backup Gateway:** Application servers use either file or block protocols.
- AWS Elastic Disaster Recovery Service:
  - Application Recovery - Service designed to protect and recover critical applications quickly at lower costs.
  - Reduced Downtimes.

## DNS, Elastic Load Balancing, and Auto Scaling

#### DNS

- Domain Name System (DNS):
  - Computers use ip addresses to connect, but people use domain names that are simple. E.g. google.com.
  - The computer reaches to the DNS server and requests for the ip address of the given domain name. If it is found, the DNS server responds with it, and them the computer connects.
- Route 53:
  - Register a domain name - public or private.
  - Use it to host website.
- Scaling Up - adding more resources to the server.
- Scaling out - more instances of the application, 

#### Auto Scaling

- Amazon Ec2 Auto Scaling:
  - Important service for maintaining the availabilty and automatic scaling of EC2 instances.
  - Automatically launch or terminate an instance.
  - Maintains availability and scale capacity.
  - Scaling is horizontal, AKA Scalling out.
  - Provides Elasticity and Scalability.
  - Responds to EC2 status checks and CloudWatch metrics.
  - Can scale based on demand.
  - Scaling policies define how to respond to changes in demand.

#### Load Balancing

- Amazon Elastic Load Balancing:
  - Provides high availabilty and fault tolerance.
  - Targets:
    - EC2 instances.
    - ECS containers.
    - IP Addresses.
    - Lambda Functions.
    - Other Load Balancers.
  