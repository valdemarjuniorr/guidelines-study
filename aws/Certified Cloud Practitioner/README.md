# AWS Certified Cloud Practitioner

## The benefits of AWS Cloud

What is the 5 criteria of cloud computing?
1. On-demand self-service
2. Access to the network
3. Resource pooling
4. Elasticity
5. Resource usage monitored and billed

### High availability, fault tolerance, and disaster recovery

#### High availability
Designing for high availability means designing for minimal downtime. Doesn't mean zero downtime. For example, when an application is down, another
application instance can start, but for that time, the application is down and not available to users.

#### Fault tolerance
Designing for fault tolerance means designing for zero downtime. For example, two server for the application are running at the same time. If one
server fails, the other server is still running and serving users.

#### disaster recovery
Designing for disaster recovery means designing for systems to operate through a disaster. For example, if a disaster occurs in one region, the
application can failover to another region.

### Scaling

There are two types of scaling:

- Vertical scaling (scaling up/down): Adding more power (CPU, RAM) to an existing server.
- Horizontal scaling (scaling out/in): Adding more servers to the existing pool of resources. The challenge with horizontal scaling is to distribute
customers session across multiple servers. This is done using load balancers or _stick session feature_ in AWS.

### Elasticity

Elasticity is the ability to automatically increase or decrease resources based on demand, using Horizontal scaling. This is done using Auto Scaling in AWS. When the demand decreases the benefit is performance efficiency, operational excellence and cost savings.

### Design principles of AWS Cloud

What is a AWS Well-Architected Framework? The Design principles:
- Stop guessing capacity;
- Test systems at production scale;
- Automate architecture;
- Allow for evolutionary changes;
- Use data to make changes;
- Improve through game days;
- Run test;

The main pillars of the AWS Well-Architected Framework are:
- Operational excellence;
- Cost optimization;
- Reliability;
- Security;
- Sustainability;
- Performance efficiency;

#### Operational Excellence
The main operations about Operational Excellence are:
- Perform operations as code;
- Make frequent, small, reversible changes;
- Refine operations procedures frequently;
- Anticipate failures;
- Learn from all operational failures;

#### Security
- Implement a strong identity foundation;
- Maintain traceability;
- Apply security at all layers;
- Automate security best practices;
- Protect data in transit and at rest;
- Keep people away from data;
- Prepare for security events;

#### Reliability
- Automate recovery procedures;
- Test recovery procedures;
- Scale horizontally to increase aggregate workload availability;
- Stop guessing capacity;
- Manage change in automation;

#### Performance Efficiency
- Democratize advanced technologies;
- Go global in minutes;
- Use serverless architectures;
- Experiment more often;
- Consider mechanical sympathy;

#### Cost Optimization
- Ability to run systems to deliver business value at the lowest price point;

#### Sustainability
- Understand your impact;
- Establish sustainability goals;
- Maximize utilization;
- Anticipate and adopt new, more efficient hardware and software offerings;
- Use managed services;
- Reduce the downstream impact of your cloud workloads;

## Understand the benefits of and strategies for migration to the AWS Cloud

The 7Rs are seven migration strategies to the cloud:
- Retire: Decommissioning servers that are no longer needed, saving upfront costs and ongoing costs;
- Retain: Keep the server without migrating to AWS cloud;
- Rehost: Migrating to AWS server without making any changes. Also known as lift and shift;
- Relocate: For a large number of servers that are made up of one or more applications;
- Repurchase: For applications with a different version or product and provides more value than the existing infrastructure. Also known as drop and
shop;
- Replatform: Move to server to AWS cloud and make change to optimize the server;
- Refactor or Well-Architect;

For migration of low latency applications to access files, the recommendation service would be Amazon EFS(file storage) and Amazon RDS(Relational
database).

For data backups the AWS options are:
- S3 Glacier;
- AWS Backup;
- Storage;

## Cloud Economics
Total cost of ownership (TCO):
- Operational expenses: day-to-day costs such as utilities, printer toner, coffee and snacks;
- Capital expenses: It's a cost associated with creating the longer-term benefits, such as purchasing a building,servers, printers and power backups.
  There are purchased once and expected to last for several years;
- Labor costs: It's for staffing an on-premises environment or data-centrers, such as the network operation center technicians to manage the
infrastructure of the servers;
- Software licensing costs;

## Security and Compliance

### Statements descriptions

Those are the 4 statements for Security and Compliance domain:

- Understand the AWS shared responsibility model;
- Understand AWS cloud security, governance, and compliance concepts;
- Identify AWS access management capabilities;
- Identify components and resources for security;

### Understand the AWS shared responsibility model;

AWS is responsible of the security of the cloud and the client is responsible for the data, permissions to each services and the applications in the cloud.

### Understand AWS cloud security, governance, and compliance concepts
Those services can help users to garantee security, governance and compliance in AWS cloud:
- Amazon CloudWatch: Which is a monitoring and observability service;
- AWS CloudTrail: Which is a service that manage, monitoring resources on AWS. For example, If you want to know to deleted a MongoDB instance, you can use CloudTrail to find out who deleted it and when;
- AWS Config: Which is a service that enables you to assess, audit, and evaluate the configurations of your AWS resources.

### Identify AWS access management capabilities

How root account in AWS is different from IAM users? The root account has full access to all AWS services and resources in the account. IAM users have
only the permissions that are granted to them by the root account or by other IAM users with appropriate permissions.

#### AWS IAM Features
- IAM users: Create users in IAM to provide access to AWS services and resources;
- IAM groups: Create groups in IAM to manage permissions for multiple users;
- IAM roles: Create roles in IAM to delegate access to AWS services and resources;
- IAM policies: Create policies in IAM to define permissions for users, groups, and roles;
- IAM integrations: IAM integrates with other AWS services to provide access control for those services;

When is preferable to use IAM roles instead of IAM users? IAM roles are preferable when you want to delegate access to AWS services and resources without sharing long-term credentials. For example, when you want to grant access to an EC2 instance to access S3 buckets, you can use an IAM role instead of creating an IAM user with access keys.

### Identify components and resources for security
The differences between Network Access Control List(ACLs) and Security Groups are:
- Network ACLs are associated with the subnet, not with the resources. They only manage traffic that cross the subnet boundary. They are stateless,
which in they only sees traffic going in one direction; If you want more directional control, you need to create rules for both inbound and outbound traffic;
- Security Groups are associated with the resources, not with the subnet. They manage traffic for the resources. They are stateful, which means that
inbound and outbound traffic are automatically allowed;

#### AWS  Security Services
- AWS WAF: It helps to control traffic with rules that you define that block common attack patterns such as SQL injections or cross-site scripting;
- AWS Trusted Advisor
- Amazon Inspector
- AWS Marketplace
- AWS Knowledge Center


## Cloud Technology and Services

### Define methods of deploying and operation in the AWS Cloud

There are some ways to deploy and operate in the AWS Cloud:
- Programmatic access;
- AWS Command line interface (CLI);
- AWS Management Console;
- Infrastructure as Code (IaC);

The differences between types of cloud computing are:

- Public cloud: A cloud environment which is available to the public that meets the cloud criteria;
- Multi-cloud: It is a public could, but use multiple cloud providers as AWS, Google Cloud and Microsoft Azure;
- Private cloud: It is when you use public and private cloud together;
- Hybrid cloud:

AWS defines as private or public cloud based on it Networks.

**QUESTION**: What do you use to connect public EC2 instances in the public subnet? An Internet Gateway or a NAT Gateway?

Internet Gateway is a horizontal scaled, redundant and highly gateway to allow communication between instances in your VPC and the public internet;
