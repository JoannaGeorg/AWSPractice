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

## Application Services  

#### Serverless Services and Event Driven Architecture

- Serverless Services:
  - No instances to manage.
  - No need to provision hardware.
  - No management of OS or software.
  - Capacity provisioning and patching is handles automatically.
  - Provides automatic scalling and high availabiltiy.
- Serverless Services in an event-driven srchitecture allows for the service to be triggered when the event occurs.
- AWS Lambda:
  - Most well-known serverless service.
  - Has functions.
  - The functions run code in response to some trigger.

#### Application Inyegration Services

- Set of services used to integrate different components of an application.
- Simple Queue Service (SQS) allows for orders to be queued when there is spike in activity until the autoscalling catches up to allow the workload.
- Simple Notifiction Service (SNS) set up, operate, and send notifications from the cloud.
- Step Functions is a coordination of AWS Services with visual workflow.
- Amazon MQ is a message broker service for Apache Active MQ and RabbitMQ.
- Amazon EventBridge is a serverless event bus for connecting applications and AWS services.

## Amazon VPC, Netwoorking, and Hybrid

#### Virtual Private Cloud:

- A VPC is a logically isolated portion of the AWS cloud within a region.
- A subnet in a VPC are mapped to an availability zone one on one.

#### Security Groups and Network ACLs

- Network ACL is a network Access Control List that is applied at the subnet level.
  - THey screen the traffic that comes into or leaves the subnet.
- Security Groups are applied at the instance level in any subnet.

#### NAT Gateways and Instances

- NAT Gateway Deployment:
  - Deployed in public subnets.
  - Have an elastic IP attatched.
  - Route to NAT Gateway added to the private subnet.
- NAT Instance:
  - Scale manulually.

#### VPC Peering

- A private network Connection between two VPCs.
- Allows VPCs to communicate as if they were on the same network.
- Uses AWS' internal network:
  - Low latency.
  - High Bandwidth.
- Key Features:
  - No Single Point of Failure.
  - No Bandwidth Bottlenecks.
  - Works Accross Accounts amd regions.
  - Full IP Adress Control.
  - Supports all AWS Services.
- Limitations:
  - No Transitive Routing,
  - Manual Foute Table Updated Required.
  - No DNS Resolution by Default.

#### VPN And AWS Direct Connect

- Connection between on-premise and cloud.
- VPN:
  - AKA AWS site-to-site VON as it connects on-premise data center to the public cloud site, VPC.
  - It is a managed IPSec VPN.
- AWS Direct Connect:
  - It is private connectivity between AWS and on-premise data center.
  - It provides consistnet network experiences.

#### AWS Transit Gateway

- *Simplified Connectivity:* Transit Gateway simplifies network management by action as a central hub that connects VPCs and on-premise networks.
- *Scalability:* It supports thousands of connectoins.
- *Transitive Routing:* Tansit Gateway allows for transitive routing - allowing VPC's to communicate with each other throughh a single central hub.
- *Integrated VPN and Cirect Connect Support:* Can be used with bothe VON and Direct connect, providing a unified gateqay for both cloud and on-premise networks.
- *Efficient Use of Route Tables:* Reduces the number of route table entries required as the VPC only need to know how to reach the transit gateway.
- *Cross-Account Access:* It can be shared across accounts using AWS RAM.


#### AWS Outposts

- Allows to run some of the AWS service in on-premise data centers.

## Deployment and Automation

#### Amazon CLoudFront

- It is a content delivery network that helps improve the performance of content that end users should be able to consume from around the world.
- Content Delivery Network (CDN) improve performance by caching content closer to the users.
- It utilizes the AWS Global Network for low latency, high performance connectivity.
- It delivers static and dynamic contnet and optimizes delivery based on content type.
- Supports live streaming and video on demand.
- Lambda@Edge enables proccessing data with Lambda functions closer to users.
- Uses HTTPS and integrates with AWS ACM for manageing SSL/TLS certificates.
- INtegrates with AWS Shield and AWS WAF for additional security protection.
- Content can also be protected with features including signed cookies, signed URLs, and origin access identity (OAI).

#### AWS Gloabal Accelarator

- Operates at the network layer - Layer 4 of OSI model.
- Provides static IP addresses as a fixed entry point to an applicatoin.
- Improves performance by leveraging the AWS global netwrok backbone, reducing internet latency and jitter.
- Performs helath checks and automatically reroutes traffic to healthy endpoints.
- Supports TCP and UDP traffic, making it suitable fot a wide range of applications, including those requiring non-HTTP protocols.
- Ideal for non-HTTP use cases such as gaming (UDP traffic), IoT, VoIP, or for services where having a static IP address id beneficial.

#### Infrastructure as Code with AWS CloudFormation

- Infrastructure patterns are defined in a template file using code.
- CloudFormation builds the infrastructure according to the provided template.

#### AWS Cloud Development Kit

- Open-source software development frameork to defnie cloud application resources usinf familiar programming languages.
- Preconfigures clous resource with provesn defaults using constructs.
- Provisions resources using AWS CloudFormation.
- Enables model application infrastructure using TypeScript, Python, Java, and .NET.

#### Platform as a Service with AWS Elastic Beanstalk

- Supports amny application platforms.
- Uses core AWS services including EC2 ECS, Auto Scalinf, and Elastic Load Balancing.
- Provides a UI to monitor and manage the health of applications.
- Managed platform updates deploy the latest versions of software and patches.
- Several Layers:
  - *Applications:* Contain environments, environment configurations, and application versions.
  - *Application Version:* A section of deployable code - will typically point to an Amazon S3 Bucket containing the code.
  - *Environments:* An applicaiton version that has been deployed on AWS resources configured and provisioned by Elastic Beanstalk.
  - *Web Servers:* Are standard applications that listen for and then process HTTP requests, typically over port 80.
  - *Workers:* are specialized applications that have a background processing task that listens for messages on an Amazon SQS queue.

#### AWS Cloud9

- IT is an integrated development environemnt.
- Used by developers to write, run, and debug code.
- Editor provides syntax highlighting, code completion, nad error checking.
- Terminal is used to navigate the file system, run commands, and mange code.
- Provides collaboration features that allow multiple developers to work on the same codebase simulataneously.
- Provides a range of debugging tools to identify and fic errors in code.
- Integrates with many AWS services.


#### AWS AppConfig

- Create, manage, and deploy application configurations.
- Capability of AWS Systems Manager.
- A cofigurations is a collection of settings that influence the behhaviour of the application.


#### AWS X-Ray

- It is a service that collects data about appliction requests, providing tools for viewing, filtering, and gaining insights.
- Key features:
  - End-to-end tracing of distributed applications.
  - Support for AWS services.
  - Real-time debugging and monitoring.

## Databases and Analytics

#### Database Types and Use Cases

- **Relational Database:**
  - Orginaized by tables, rows, and columns.
  - Rigid schema (SQL).
  - Rules enforeces within database.
  - Typically scaled vertically.
  - Supports complex queries and joins.
  - Eg. Amazon RDS, Oracle, MySQLl, IBM DB2, PostgreSQL.
- **Non-Relational Database:**
  - Varied data storage models.
  - Flexible schema (NoSQL) - datastored in key-value pairs, columns, documents, or graphs.
  - Scales horizontally.
  - Unstructured, simple language that supports any kind of schema.
  - Amazon DynamoDB, Mongo DB, Redis, NEO4j.
- **Operational/Transactional:**
  - Online Transaction Processing (OLTP).
  - Productoin DBs that process transactions.
  - Short Transactions and simple queries.
  - Eg:
    - Realtional: amazon RDs, Oracle, IBM DB2, MySQL.
    - NON-Relational: MongoDB, Cassandra, NEO3j, and HBase.
- **Analytical Databse:**
  - ONline Analytics Processing (OLAP) - the source of thedata comes from OLTP DBs.
  - Data Warehouse - Typicallt separated from the customer facing DBs.
  - Long Transactions and complex queries.
  - Eg:
    - Relational: Mazon RedShift, Teradata, HP Vertica.
    - Non-Realtional: Amazon EMR, MapReduce.

#### Amazon Relational Database Service (RDS)

- Managed Realtional database service.
- Used for online transcation processing (OLTP) use cases.
- Runs on Amazon EC2 Instances.
- Amazon Aurora is a MYSQL, PostgreSQL compatible realtional data base built for the cloud.

#### Amazon DynamoDB

- Fully managed NoSQL databse service.
- Fully serverless service.
- Key/value store and document sotre/
- Low Latency access to data.
- Offers puxh button scaling with no downtime.

#### Amazon ReadShift

- It is a fast, fully amanged data warehouse that makes it simple and cost-effective to analyze all your data using standard SQL and existing Business Intelligence (BI) Tools.
- It is a SQL based data warebouse used for analytics applications.
- It is a relational databse that is used for Online Analytics Processing (OLAP) use cases.

#### Amazon EMR (Elastic Map Reduce)

- Managed cluster platform that simplifies running big data frameworkd including Apache Hadoop and Apache Spark.
- Used for processing data for analytics and business intelligence.
- Can also be used for transforming and moving large anmounts of data.

#### Amzon ElastiCache

- Fully managed implementations Redis and Memcached.
- Is a key-value store.
- In-memory databse offereing high performance and low latency.

#### Amazon Athena

- Athena queries in s3 using SQL.
- Can be connected to othher data sources with Lambda.
- Data can be in CSV, TSV, JSON, Parquet, and ORC formats.
- Uses a managed Data Catalog (AWS Glue) to store information and schhems anout the databases and tables.

#### Amazon OpenSearch Service

- Distributed sercha dn analytics suite.
- Based on the popular open source Elasticsearch.
- Supports queries using SQL syntax.
- Integrates with open-cource tools.
- Scale by adding or removing instances.
- Availability in up to 3 Availability zones.
- Bacjup using SnapShots.
- Encryption at-rest and in-transit.

#### AWS Data Exchange

- It is a platform that facilitates the secure exchange and use of data products, including 3rd party data.
- Extensive Data sets - 3,500+ data sets from 300+ rpoviders.
- Used for Business Inteligence, and Machine Learning.
