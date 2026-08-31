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

