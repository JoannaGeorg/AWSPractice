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
    