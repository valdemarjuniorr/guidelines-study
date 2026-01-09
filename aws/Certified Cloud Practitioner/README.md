# AWS Certified Cloud Practitioner

## The benefits of AWS Cloud

What is the 5 criteria of cloud computing?
1. On-demand self-service
2. Access to the network
3. Resource pooling
4. Elasticity
5. Resource usage monitored and billed

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

### Define the AWS global infrastructure

Global resilience services are:
- Route 53
- CloudFront
- IAM

Region resilience services are:
- AWS AMF
- AWS Batch

Availability Zone resilience services are:
- Amazon ABS
- AWS EC2

### Structure of AWS global infrastructure
- `Availability Zone(AZ)`: AZ is one or more data centrers with redundant power, networking and connectivity and so on; In every AZ are Data Centrers;
  If a AZ fails, the others AZs should keep the services running, because they are isolated from each other. AZs are connected to each other with low latency links;
- `Region`: A geographical area that contains a collection of Availability Zones; Each region is fault tolerant;
- `Wavelength`: It parts of a region. It has a Wavelength zone which is an isolated zone in the carrier location; Wavelength zones are tied to an AWS region and are extensions lie the Local Zones;
- `Edge Locations`: Its a global service that cache content closer to end users to reduce latency; Edge Locations are used by CloudFront and Route 53;

### AWS Compute Services

#### AWS EC2
AWS EC2 is a web service that provides resizable compute capacity in the cloud which is is launch into a specific subnet inside your Amazon VPC. It is designed to make web-scale cloud computing easier for developers. EC2 host access and manage the EC2 instance and it is within a AZ. If the AZ fails, the EC2 host and the EC2 instance will fail too. For networking it is possible to connect different Elastic Network Interfaces (ENI) to an EC2 instance.

The AZ there is a Storage Network which is used to connect EC2 instances to EBS volumes. Those ENI are not allows to access others ENI or EBS from
another AZ.

#### High availability and scalability
There are those services responsible to Load balancers(LB) and Auto Scaling Groups(ASG):

- Classic Load Balancer (CLB): It is used to distribute incoming application traffic across multiple EC2 instances in multiple AZs;
- Application Load Balancer (ALB): It is used to route traffic to different services based on the content of the request;
- Network Load Balancer (NLB): It is used to handle millions of requests per second while maintaining ultra-low latencies;
- Gateway Load Balancer (GLB): It is used to deploy, scale, and manage virtual appliances such as firewalls, intrusion detection and prevention systems, and deep packet inspection systems;

When you create a LB, you are creating an entity, one load balancer, but actually creates an ELB node in each AZ that you enable.

## AWS database resources

Those are the four statements for AWS database services:
- Amazon RDS: Are database as a service which the user don't need to manage the database software or hardware.
- Amazon Aurora: Is a relational database engine that combines the speed and availability of high-end commercial databases with the simplicity and cost-effectiveness of open source databases as postgres and mysql. The main benefits of Amazon Aurora of Amazon RDS is Aurora shares cluster storage volume and not local storage.
- Amazon DynamoDB: Is a key-value and document database that delivers single-digit millisecond performance. It is a not a relational database. It
support scale-out architecture automatically;
  - In Memory Database Services: Amazon ElastiCache and Amazon DynamoDB Accelerator (DAX) are the main services for in-memory databases. They are used to improve the performance of web applications by retrieving data from high throughput and low latency in-memory data stores.
- Amazon Redshift: Is a fully managed data warehouse that makes it simple and cost-effective to analyze all your data using standard SQL and your existing Business Intelligence (BI) tools. It is used for online analytical processing (OLAP) and big data applications. It based on postgres, but not use it for transactional databases.

### Database migration tools

Those are the the migration tools available in AWS:
- AWS SnowFamily: They are a collections of services to help users to migrate the large amount of data to AWS cloud. The main services are Snowcone, Snowball and Snowmobile;
- AWS DAtabase Migration Services (DMS): Manage database migration and schema conversion. This replication process is very admin intensive; The user
create a source and a target endpoint(replica) and DMS manage the replication process;
- AWS Schema Conversion Tool (SCT): It is used to convert the database schema from one database engine to another. For example, from Oracle to Amazon Aurora.
- AWS DataSync: It is used to automate and accelerate moving data between on-premises storage and AWS storage services as S3, EFS and FSx for Windows File Server;

## AWS Network resources

Amazon VPC is a virtual network dedicated to your AWS account. It is logically isolated from other virtual networks in the AWS Cloud. You can launch your AWS resources, such as Amazon EC2 instances, into your VPC. It is possible to connect AWS VPC to an on-premises network using AWS Direct Connect or a VPN connection. By defaulot, each VPC is private and isolated. Every VPC has a router that is high available.

## AWS Storage resources

Types of storage in AWS:
- Object Storage: Amazon S3 and Amazon Glacier; Global resilience storage; S3 is replicated across multiple AZs in that region; A bucket must have
unique name across all AWS accounts;
  - S3 Glacier Deep Archive is the lowest cost storage class and support long term retention within 12 hours of retrieval time;
- File Storage: Amazon EFS and Amazon FSx; It is ideal for use cases like large content repositories, development environments, media stores, and home directories. EFS is used for linux distro. It is not allowed to use EFS for windows; Instead use FSx for windows files systems; Lustre is used for high performance computing (HPC) and machine learning (ML) workloads that require fast storage with high levels of throughput and IOPS;
- Block Storage: Amazon EBS and Instance Store. It is very resilience and is separate from the instance hardware. It is recommended for the most
system boot volumes;

## AWS Artificial Intelligence (AI) and Machine Learning (ML) services

For ML there are those services:
- Artificial Intelligence (AI) Services: Those services provide pre-trained AI models that are ready to use for developers with no ML expertise. The main services are Amazon Rekognition, Amazon Polly, Amazon Lex, Amazon Comprehend and Amazon Transcribe;
- Machine Learning (ML) Services: Those services provide a platform for developers and data scientists to build, train, and deploy ML models. The main services are Amazon SageMaker, AWS Deep Learning AMIs, AWS DeepRacer and AWS DeepLens;
- ML Frameworks and Infrastructure: Those services provide a platform for developers and data scientists to build, train, and deploy ML models using popular ML frameworks. The main services are TensorFlow, PyTorch, Apache MXNet, Chainer and Keras;

## Identify services from other in-scope AWS services categories

- Amazon EventBridge is a serverless event bus that makes it easy to connect applications using data from your own applications, integrated
Software-as-a-Service (SaaS) applications, and AWS services. EventBridge delivers a stream of real-time data from event sources, such as Zendesk, Datadog, or PagerDuty, and routes that data to targets like AWS Lambda.
- Amazon Connect is an easy-to-use omnichannel cloud contact center that helps companies provide superior customer service at a lower cost. With Amazon Connect, you can set up a contact center in just a few clicks and start providing better service to your customers.
- Customer engagement services: Amazon Pinpoint and Amazon Simple Email Service (SES) are the main services for customer engagement. They are used to engage with customers through email, SMS, push notifications, and voice messages.
  - AWS Activate: It is a program that provides startups with the resources they need to build and grow their businesses on AWS. It offers benefits such as AWS credits, training, technical support, and access to a global network of entrepreneurs and investors.
  - AWS IQ: It is a service that connects AWS customers with AWS Certified third-party experts for on-demand project work. It helps customers find the right expert for their specific needs and provides a secure platform for collaboration and payment.
  - AWS Managed Services (AMS): It is a service that helps customers manage their AWS infrastructure and applications. It provides a range of services, including monitoring, patching, backup, and security management, to help customers optimize their AWS environment and reduce operational overhead.
  - AWS Support: They are a range of support plans that provide customers with access to AWS technical support and guidance. The main support plans are Basic, Developer, Business, and Enterprise.
- AWS Developer services: They are a range of services that help developers build, test, and deploy applications on AWS. The main services are AWS CodeCommit, AWS CodeBuild, AWS CodeDeploy, and AWS CodePipeline.
- AWS end-user computing services: They are a range of services that provide virtual desktops and applications to end-users. The main services are Amazon WorkSpaces and Amazon AppStream 2.0.
- AWS Frontend web and mobile services: They are a range of services that help developers build, deploy, and manage web and mobile applications on AWS. The main services are AWS Amplify, Amazon API Gateway, and AWS AppSync.
- AWS IoT Services: They are a range of services that help developers build, deploy, and manage IoT applications on AWS. The main services are AWS IoT Core, AWS IoT Greengrass, and AWS IoT Analytics.

## Introduction to billing, pricing and support

### Compare AWS pricing models
Cost optimization has an ability to run systems to deliver business value at the lowest price point. There are some services to help users to optimize costs in AWS:
- AWS Budgets: It is used to set custom cost and usage budgets that alert you when you exceed your thresholds;
- AWS Cost and Usage Report: It is used to create detailed reports about your AWS costs and usage;

AWS also provides cost effective resources like Spot instances, Reserved instances and cost-effective storage like Amazon S3 Glacier and S3 Glacier Archive.

### AWS cost optimization
- Right sizing: It is the process of matching instance types and sizes to your workload requirements to optimize performance and cost;
- Increasing elasticity: It is the process of using Auto Scaling to automatically adjust capacity to maintain steady, predictable performance at the lowest possible cost;
- Choose the right pricing model: It is the process of selecting the most cost-effective pricing model for your workloads, such as On-Demand,
Reserved, or Spot Instances. Spot instances are the cheapest option, but they can be interrupted by AWS with a two-minute warning when AWS needs the capacity back;

### Pillars of Cost optimization
- Right-sizing;
- Match storage to usage;
- Data transfer;
- Measure, monitor and improve;

### Billing, budgets and cost management

- AWS Cost Exporter: It is a tool that enables you to view and analyze your AWS costs and usage. It provides detailed reports that can help you identify cost-saving opportunities and optimize your AWS spending.
- AWS Cost and Usage Report: It is a tool that provides detailed information about your AWS costs and usage. It allows you to create custom reports
that can help you understand your spending patterns and identify areas for cost optimization.
- AWS Billing Conductor: It is a tool that helps you manage your AWS billing and payments. It provides features such as consolidated billing, cost allocation tags, and payment methods to help you streamline your billing processes and optimize your AWS spending.

