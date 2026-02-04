# AWS Certified Cloud Practitioner

---

## The Benefits of AWS Cloud

There are those benefits when using AWS Cloud:
- You pay as you go;
- Benefit from massive economies of scale; AWS buy hardware in bulk and pass the savings to the customers;
- Stop guessing capacity;
- Increase speed and agility;
- Stop spending money on running and maintaining data centers;
- Go global in minutes;

### What are the 5 Criteria of Cloud Computing?

1. On-demand self-service
2. Access to the network
3. Resource pooling
4. Elasticity
5. Resource usage monitored and billed

---

### High Availability

Designing for high availability means designing for minimal downtime. It doesn't mean zero downtime. For example, when an application is down, another application instance can start, but during that time, the application is down and not available to users.

---

### Fault Tolerance

Designing for fault tolerance means designing for zero downtime. For example, two servers for the application are running at the same time. If one server fails, the other server is still running and serving users.

---

### Disaster Recovery

Designing for disaster recovery means designing for systems to operate through a disaster. For example, if a disaster occurs in one region, the application can failover to another region.

---

### Scaling

There are two types of scaling:

- **Vertical scaling (scaling up/down)**: Adding more power (CPU, RAM) to an existing server.
- **Horizontal scaling (scaling out/in)**: Adding more servers to the existing pool of resources. The challenge with horizontal scaling is to distribute customers' sessions across multiple servers. This is done using load balancers or _sticky session feature_ in AWS.

---

### Elasticity

Elasticity is the ability to automatically increase or decrease resources based on demand, using horizontal scaling. This is done using `Auto Scaling` in AWS. When the demand decreases, the benefit is performance efficiency, operational excellence, and cost savings.

---

### Design Principles of AWS Cloud

#### What is the AWS Well-Architected Framework?

**Design Principles:**
- Stop guessing capacity
- Test systems at production scale
- Automate architecture
- Allow for evolutionary changes
- Use data to make changes
- Improve through game days
- Run tests

**The Main Pillars of the AWS Well-Architected Framework:**
- Operational excellence
- Cost optimization
- Reliability
- Security
- Sustainability
- Performance efficiency

---

#### Operational Excellence

The main operations about Operational Excellence are:
- Perform operations as code
- Make frequent, small, reversible changes
- Refine operations procedures frequently
- Anticipate failures
- Learn from all operational failures

---

#### Security

- Implement a strong identity foundation
- Maintain traceability
- Apply security at all layers
- Automate security best practices
- Protect data in transit and at rest
- Keep people away from data
- Prepare for security events

---

#### Reliability

- Automate recovery procedures
- Test recovery procedures
- Scale horizontally to increase aggregate workload availability
- Stop guessing capacity
- Manage change in automation

---

#### Performance Efficiency

- Democratize advanced technologies
- Go global in minutes
- Use serverless architectures
- Experiment more often
- Consider mechanical sympathy

---

#### Cost Optimization

- Ability to run systems to deliver business value at the lowest price point

---

#### Sustainability

- Understand your impact
- Establish sustainability goals
- Maximize utilization
- Anticipate and adopt new, more efficient hardware and software offerings
- Use managed services
- Reduce the downstream impact of your cloud workloads

---

## Understand the Benefits of and Strategies for Migration to the AWS Cloud

- **`AWS CAF`**: The Cloud Adoption Framework(CAF) a framework that brings AWS experience and best practices to companies preparing to migrate to the AWS. It provides tools to help accelerate the migration journey, organize resources, and align management during the transition. The main perspectives are Business, People, Governance, Platform, Security, and Operations.

### The 7Rs Migration Strategies

The 7Rs are seven migration strategies to the cloud:

- **Rehost**: Migrating to AWS server without making any changes. Also known as "lift and shift";
- **Relocate**: For a large number of servers that are made up of one or more applications;
- **Replatform**: Move to server to AWS cloud and make changes to optimize the server. Also known as "lift, tinker and shift";
- **Refactor or Well-Architect**: Complete redesign and refactoring your application fully or the infrastructure;
- **Repurchase**: It involves moving from a traditional license to a Software-as-a-Service(SaaS) model. For example, a business might choose to implement the repurchansing strategy by migration from a CRM systems to a new sales force software.
- **Retain**: Keep the server without migrating to AWS cloud;
- **Retire**: Decommissioning servers that are no longer needed, saving upfront costs and ongoing costs;

For migration of low latency applications to access files, the recommended service would be `Amazon EFS` (file storage) and `Amazon RDS` (Relational database).

### Migration services and tools

- **`Migration Evaluator`**: It is a migration assessment service that helps you create a business case for AWS planning and migration. It is the
beginning of your migration process;
- **`AWS Application Discovery`**: It helps _enterprise customers plan migration_ projects by gathering information about their on-premises data centers;
- **`Migration Hub`**: It is a centralized hub to take you from discovery, assessment, planning, and execution of your migration. It provides tools, guidance and automated recommendations to collaborate with your team and track your migration;
- **`Application Migration Service`**: it a tool to move and improve your on-premises and cloud-based applications. It helps customers streamline,
expedite and reduce the cost of migrating and modernizing applications;

### Data Backup Options

For data backups, the AWS options are:
- `S3 Glacier`
- `AWS Backup`
- Storage

---

## Cloud Economics

### Total Cost of Ownership (TCO)

- **Operational expenses**: Day-to-day costs such as utilities, printer toner, coffee, and snacks
- **Capital expenses**: Costs associated with creating longer-term benefits, such as purchasing a building, servers, printers, and power backups. These are purchased once and expected to last for several years
- **Labor costs**: Staffing for an on-premises environment or data centers, such as the network operation center technicians to manage the infrastructure of the servers **Software licensing costs**

---

## Security and Compliance

### Statement Descriptions

These are the 4 statements for the Security and Compliance domain:

- Understand the AWS shared responsibility model
- Understand AWS cloud security, governance, and compliance concepts
- Identify AWS access management capabilities
- Identify components and resources for security

### Authentication vs Authorization

Authentication is responsible to identify of a user or entity through credentials. Authorization is responsible to granting authenticated users with
certain access to rights and permissions to resources.

All authorization are denied by default and the _least privilege principle_ must be applied. It means that a user is granted access only to what
they needed.

#### AWS IAM Features

- **IAM users**: Create users in `IAM` to provide access to AWS services and resources;
- **IAM groups**: Create groups in `IAM` to manage permissions for multiple users;
- **IAM roles**: Create roles in `IAM` to delegate access to AWS services and resources. This role can assume to gain a temporary access to
permissions;
- **IAM policies**: Create policies in `IAM` to define permissions for users, groups, and roles;
- **IAM integrations**: `IAM` integrates with other AWS services to provide access control for those services;

**When is it preferable to use IAM roles instead of IAM users?**

`IAM` roles are preferable when you want to delegate access to AWS services and resources without sharing long-term credentials. For example, when you want to grant access to an `EC2` instance to access `S3` buckets, you can use an `IAM` role instead of creating an `IAM` user with access keys.

To centralize your credentials and API keys on AWS there is the service called **`AWS Secrets Manager`**. It helps you protect access to your applications, services, and IT resources without the upfront cost and complexity of managing your own hardware security module (HSM) infrastructure.

**QUESTION**

What an application hosted in AWS can do to avoid DDos(Distributed Denial of Service) attacks?

_Security groups make sure only traffic from authenticated users is allowed into the system, while an ELB distributes incoming traffic to prevent any single frontend server from being overwhelmed. Operating at the AWS network level, these components leverage the full capacity of the AWS Region to help absorb large-scale attacks._

#### Detection and response services

Those are the main services for detection and response in AWS:

- **`Amazon Inspector`**: It helps improve the security and compliance of applications by running automated security assessments for EC2 instances, containers, and Lambada functions;
- **`Amazon GuardDuty`**: It is a threat detection service that continuously monitors for malicious activity and unauthorized behavior to protect AWS accounts and workloads;
- **`Amazon Detective`**: After the threat has been detected, you can use it to further investigate the root cause. It helps you analyze threats with interactive visualizations contained in a unified AWS Management Console.
- **`Amazon Security Hub`**: It brings multiple security services together into a single place and format. You can quickly see your security and compliance state in one comprehensive view.
- **`Amazon Shield`**: It is managed DDoS protection service that safeguards applications running on AWS from common, frequently occurring types of DDoS attacks at no cost;

---

### Understand the AWS Shared Responsibility Model

AWS is responsible for the security **of** the cloud, and the client is responsible for the data, permissions to each service, and the applications in the cloud.

---

### Identify AWS Access Management Capabilities

**How is the root account in AWS different from IAM users?**

The root account has full access to all AWS services and resources in the account. `IAM` users have only the permissions that are granted to them by the root account or by other `IAM` users with appropriate permissions.

---

### Identify Components and Resources for Security

**The differences between Network Access Control Lists (ACLs) and Security Groups:**

- **Network ACLs**: Associated with the subnet, not with the resources. They only manage traffic that crosses the subnet boundary. They are stateless, which means they only see traffic going in one direction. If you want more directional control, you need to create rules for both inbound and outbound traffic. Every single packet that crosses its border regardless any circumstance will be evaluated against the rules in the ACL.
- **Security Groups**: Associated with the resources, not with the subnet. They manage traffic for specific AWS resources. They are stateful, which means that inbound and outbound traffic are automatically allowed

#### AWS Security Services

- **`AWS WAF(Web Application Firewall)`**: It Helps to control traffic with rules that you define that block common attack patterns such as SQL injections or cross-site scripting
- **`AWS Trusted Advisor`**: It is a service that you can use that evaluate your resources against five categories: cost optimization, performance, security, fault tolerance, and service limits;
- **`Amazon Inspector`**
- **`AWS Marketplace`**
- **`AWS Knowledge Center`**

---

## Cloud Technology and Services

### Define Methods of Deploying and Operating in the AWS Cloud

There are some ways to deploy and operate in the AWS Cloud:

- Programmatic access
- AWS Command Line Interface (CLI)
- AWS Management Console
- Infrastructure as Code (IaC)

### Types of Cloud Computing

The differences between types of cloud computing are:

- **Public cloud**: A cloud environment which is available to the public that meets the cloud criteria
- **Multi-cloud**: A public cloud, but uses multiple cloud providers such as AWS, Google Cloud, and Microsoft Azure
- **Private cloud**: A cloud environment that is used exclusively by a single organization
- **Hybrid cloud**: When you use public and private cloud together

AWS defines as private or public cloud based on its networks.

**QUESTION**: What do you use to connect public `EC2` instances in the public subnet? An Internet Gateway or a NAT Gateway?

**Answer**: Internet Gateway is a horizontally scaled, redundant, and highly available gateway to allow communication between instances in your VPC and the public internet.

---

### Define the AWS Global Infrastructure

**Global resilience services:**
- `Route 53`
- `CloudFront`
- `IAM`

**Region resilience services:**
- `AWS AMF`
- `AWS Batch`

**Availability Zone resilience services:**
- `Amazon ABS`
- `AWS EC2`

---

### Structure of AWS Global Infrastructure

- **`Availability Zone (AZ)`**: An AZ is one or more data centers with redundant power, networking, and connectivity. In every AZ are data centers. If an AZ fails, the other AZs should keep the services running because they are isolated from each other. AZs are connected to each other with low latency links.
- **`Region`**: A geographical area that contains a collection of Availability Zones. Each region is fault tolerant.
- **`Wavelength`**: Part of a region. It has a Wavelength zone which is an isolated zone in the carrier location. Wavelength zones are tied to an AWS region and are extensions like the Local Zones.
- **`Edge Locations`**: A global service that caches content closer to end users to reduce latency and they are located outside of AWS regions. Edge Locations are used by `CloudFront` and `Route 53`.

---

### AWS Compute Services

#### AWS EC2

`AWS EC2` is a web service that provides resizable compute capacity in the cloud, which is launched into a specific subnet inside your `Amazon VPC`. It is designed to make web-scale cloud computing easier for developers. `EC2` hosts access and manage the `EC2` instance, and it is within an AZ. If the AZ fails, the `EC2` host and the `EC2` instance will fail too. For networking, it is possible to connect different Elastic Network Interfaces (ENI) to an `EC2` instance.

In the AZ, there is a Storage Network which is used to connect `EC2` instances to `EBS` volumes. Those ENIs are not allowed to access other ENIs or `EBS` from another AZ.

**QUESTION**

What is multi-tenancy in context of AWS EC2 instances?
Multi-tenancy allows multiple virtual machines to sahre resources on the same physical host, with isolation between them.

##### Instance Types

- **Memory Optimized**: It is designed for high-memory workloads and offer the performance needed to handle large volumes of data efficiently, making
them the best choice for real-time analytics;
- **Storage Optimized**: It is designed for workloads that require high-disk throughput and low-latency access to large datasets. This makes them the best
  choice for data analytics applications;
- **Savings Plans**: It is designed for critical workloads that need consistent capacity and predictable pricing;
- **Spot Instances**: It is designed for flexible, interruption-tolerant workloads. It is the most cost-effective option, but it can be interrupted by AWS;
- **Reserved Instances**: It is designed for applications with steady-state or predictable usage. It provides a significant discount (up to 75%) compared to On-Demand pricing;

---

#### High Availability and Scalability

These are the services responsible for Load Balancers (LB) and Auto Scaling Groups (ASG):

- **Classic Load Balancer (CLB)**: Used to distribute incoming application traffic across multiple `EC2` instances in multiple AZs
- **Application Load Balancer (ALB)**: Used to route traffic to different services based on the content of the request
- **Network Load Balancer (NLB)**: Used to handle millions of requests per second while maintaining ultra-low latencies
- **Gateway Load Balancer (GLB)**: Used to deploy, scale, and manage virtual appliances such as firewalls, intrusion detection and prevention systems, and deep packet inspection systems

When you create an LB, you are creating an entity, one load balancer, but it actually creates an ELB node in each AZ that you enable.

---

## AWS Database Resources

These are the four main AWS database services:

### Amazon RDS

Database as a service where the user doesn't need to manage the database software or hardware. Amazon RDS automatically handles patching as part of its managed services offering over AZs. Self-managed patching would increase operational overhead rather than reduce it, which defeats one of the main benefits of using it.

### Amazon Aurora

A relational database engine that combines the speed and availability of high-end commercial databases with the simplicity and cost-effectiveness of open-source databases such as PostgreSQL and MySQL. The main benefit of `Amazon Aurora` over `Amazon RDS` is that Aurora shares cluster storage volume and not local storage.

### Amazon DynamoDB

A key-value and document database that delivers single-digit millisecond performance. It is not a relational database. It supports scale-out architecture automatically.

#### In-Memory Database Services

`Amazon ElastiCache` and `Amazon DynamoDB Accelerator (DAX)` are the main services for in-memory databases. They are used to improve the performance of web applications by retrieving data from high throughput and low latency in-memory data stores.

### Amazon Redshift

A fully managed data warehouse that makes it simple and cost-effective to analyze all your data using standard SQL and your existing Business Intelligence (BI) tools. It is used for online analytical processing (OLAP) and big data applications. It is based on PostgreSQL, but don't use it for transactional databases.

### Amazon Neptune

A fully managed, purpose-built graph database service that manages highly connnected data sets, like those used in social networking applications. It
excels at understanding complex relationships that are difficult to identify in traditional relational databases like user connections, friends
networks and interaction patterns.

---

### Database Migration Tools

These are the migration tools available in AWS:

- **`AWS Snow Family`**: A collection of services to help users migrate large amounts of data to AWS cloud. The main services are Snowcone, Snowball, and Snowmobile.
- **`AWS Database Migration Service (DMS)`**: Manages database migration and schema conversion. This replication process is very admin intensive. The user creates a source and a target endpoint (replica), and DMS manages the replication process.
- **`AWS Schema Conversion Tool (SCT)`**: Used to convert the database schema from one database engine to another. For example, from Oracle to `Amazon Aurora`.
- **`AWS DataSync`**: Used to automate, schedule and accelerate moving data between on-premises storage and AWS storage services such as `S3`, `EFS`, and `FSx for Windows File Server`.
- **`AWS Transfer Family`**: It makes possible to seamlessly manage and share data with simple, secure and scalable file transfers. This service
provides fully managed support for secure file transfer over FTP, Secure File Transfer protocol(SFTP) and other protocols;
---

## AWS Network Resources

`Amazon VPC` is a virtual network dedicated to your AWS account. It is logically isolated from other virtual networks in the AWS Cloud. You can launch your AWS resources, such as `Amazon EC2` instances, into your VPC. It is possible to connect `AWS VPC` to an on-premises network using `AWS Direct Connect` or a VPN connection. By default, each VPC is private and isolated. Every VPC has a router that is highly available.

---

## AWS Storage Resources

### Types of Storage in AWS

#### Object Storage

- **`Amazon S3`** and **`Amazon Glacier`**: Global resilience storage. `S3` is replicated across multiple AZs in that region. A bucket must have a unique name across all AWS accounts.
  - **`S3 Glacier Deep Archive`**: The lowest cost storage class and supports long-term retention within 12 hours of retrieval time.

#### File Storage

- **`Amazon EFS`** and **`Amazon FSx`**: Ideal for use cases like large content repositories, development environments, media stores, and home directories. `EFS` is used for Linux distributions. It is not allowed to use `EFS` for Windows; instead, use `FSx for Windows File Server`. `Lustre` is used for high-performance computing (HPC) and machine learning (ML) workloads that require fast storage with high levels of throughput and IOPS. It can be accessed by multiple `EC2` instances at the same time.

#### Block Storage

- **`Amazon EBS`** and **Instance Store**: Very resilient and is separate from the instance hardware. It is recommended for most system boot volumes.
  It provides high availability and durability by automatically replicating volumes within the same AZ.

**`EBS snapshots`** are point-in-time copies of EBS volumes that can be used for regular backups, creating duplicate volumes for testing, and enabling fast
disaster recovery by restoring entire volumes from snapshots.

### AWS Storage Gateway

There are three types of storage gateways:

- **File Gateway**: Used for file-based workloads. It provides a file interface to store files as objects in `S3` using the NFS and SMB protocols.
- **Volume Gateway**: Used for block-based workloads. It provides block storage to on-premises applications using the iSCSI protocol.
- **Tape Gateway**: Used for backup and archival workloads. It provides a virtual tape library (VTL) interface to store backup data in `S3` and
`Glacier`.

### AWS Data Lifecycle Manager

It is used to automate the creating, retention, and deletion of EBS snapshots and EBS backed Amazon Machine Images (AMIs) according to a schedule
defined in lifecycle polices.

---

## AWS Artificial Intelligence (AI) and Machine Learning (ML) Services

With ML training is possible a model that can be applied to new data to make predictions or decisions based on the patterns it is learned. For ML, there are these services:

### Artificial Intelligence (AI) Services

These services provide pre-trained AI models that are ready to use for developers with no ML expertise. The main services are `Amazon Rekognition`, `Amazon Polly`, `Amazon Lex`, `Amazon Comprehend`, and `Amazon Transcribe`.

### Machine Learning (ML) Services

These services provide a platform for developers and data scientists to build, train, and deploy ML models. The main services are `Amazon SageMaker`, `AWS Deep Learning AMIs`, `AWS DeepRacer`, and `AWS DeepLens`.

### ML Frameworks and Infrastructure

These services provide a platform for developers and data scientists to build, train, and deploy ML models using popular ML frameworks. The main services are `TensorFlow`, `PyTorch`, `Apache MXNet`, `Chainer`, and `Keras`.

---

## Identify Services from Other In-Scope AWS Service Categories

### Event-Driven Services

- **`Amazon EventBridge`**: A serverless event bus that makes it easy to connect applications using data from your own applications, integrated Software-as-a-Service (SaaS) applications, and AWS services. EventBridge delivers a stream of real-time data from event sources, such as Zendesk, Datadog, or PagerDuty, and routes that data to targets like `AWS Lambda`.

### Customer Service and Engagement

- **`Amazon Connect`**: An easy-to-use omnichannel cloud contact center that helps companies provide superior customer service at a lower cost. With `Amazon Connect`, you can set up a contact center in just a few clicks and start providing better service to your customers using AI.
- **Customer engagement services**: `Amazon Pinpoint` and `Amazon Simple Email Service (SES)` are the main services for customer engagement. They are used to engage with customers through email, SMS, push notifications, and voice messages.

### AWS Support Programs

- **`AWS Activate`**: A program that provides startups with the resources they need to build and grow their businesses on AWS. It offers benefits such as AWS credits, training, technical support, and access to a global network of entrepreneurs and investors.
- **`AWS IQ`**: A service that connects AWS customers with AWS Certified third-party experts for on-demand project work. It helps customers find the right expert for their specific needs and provides a secure platform for collaboration and payment.
- **`AWS Managed Services (AMS)`**: A service that helps customers manage their AWS infrastructure and applications. It provides a range of services, including monitoring, patching, backup, and security management, to help customers optimize their AWS environment and reduce operational overhead.
- **`AWS Support`**: A range of support plans that provide customers with access to AWS technical support and guidance. The main support plans are Basic, Developer, Business, and Enterprise.

### Development and Deployment Services

- **AWS Developer services**: A range of services that help developers build, test, and deploy applications on AWS. The main services are `AWS CodeCommit`, `AWS CodeBuild`, `AWS CodeDeploy`, and `AWS CodePipeline`.

### End-User Computing

- **AWS end-user computing services**: A range of services that provide virtual desktops and applications to end-users. The main services are `Amazon WorkSpaces` and `Amazon AppStream 2.0`.

### Frontend Web and Mobile

- **AWS Frontend web and mobile services**: A range of services that help developers build, deploy, and manage web and mobile applications on AWS. The main services are `AWS Amplify`, `Amazon API Gateway`, and `AWS AppSync`.

### Internet of Things (IoT)

- **AWS IoT Services**: A range of services that help developers build, deploy, and manage IoT applications on AWS. The main services are `AWS IoT Core`, `AWS IoT Greengrass`, and `AWS IoT Analytics`.

---

## Introduction to Billing, Pricing, and Support

Pricing factors into numerous service categories, but the driving factors of cost are compute, storage, and data transfer.

### AWS Cost Optimization

- **Right sizing**: The process of matching instance types and sizes to your workload requirements to optimize performance and cost.
- **Increasing elasticity**: The process of using `Auto Scaling` to automatically adjust capacity to maintain steady, predictable performance at the lowest possible cost.
- **Choose the right pricing model**: The process of selecting the most cost-effective pricing model for your workloads, such as On-Demand, Reserved, or Spot Instances. Spot instances are the cheapest option, but they can be interrupted by AWS with a two-minute warning when AWS needs the capacity back.

AWS also provides cost-effective resources like Spot instances, Reserved instances, and cost-effective storage like `Amazon S3 Glacier` and `S3 Glacier Archive`.

---

### Pillars of Cost Optimization

- Right-sizing
- Match storage to usage
- Data transfer
- Measure, monitor, and improve

---

### Billing, Budgets, and Cost Management

Cost optimization has the ability to run systems to deliver business value at the lowest price point. There are some services to help users optimize costs in AWS:

- **`AWS Cost Explorer`**: A tool that enables you to view and analyze your AWS costs and usage. It provides detailed reports that can help you identify cost-saving opportunities and optimize your AWS spending.
- **`AWS Cost and Usage Report`**: A tool that provides detailed information about your AWS costs and usage. It allows you to create custom reports that can help you understand your spending patterns and identify areas for cost optimization.
- **`AWS Billing Conductor`**: A tool that helps you manage your AWS billing and payments. It provides features such as consolidated billing, cost allocation tags, and payment methods to help you streamline your billing processes and optimize your AWS spending.
- **`AWS Budgets`**: A tool that helps to monitor reservation utilization and trigger alerts when it drops below the defined threshold.

When it comes to AWS pricing, customers pay as they go and can save when they commit to a specific amount of usage for a certain period of time. They can also get volume-based discounts as their usage increases.

---

## Networking

Amazon VPC lets you provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you define.
The benefits of using `Amazon VPC` are:
- **Increase security**;
- **Save time**;
- **Control environment**;

A virtual private gateway is the component that allows protected internet traffic to enter into the VPC. This is perfect to restrict access to only
protected internet traffic.

Those are the definitions of key networking components in AWS:
- **Subnet**: A range of IP addresses in your VPC. You can launch AWS resources into a specified subnet. It can be public or private.
 - **private subnet**: A subnet that is not connected to the internet. For example, a database server.
 - **public subnet**: A subnet that is connected to the internet. For example, a web server or web site.

To allow traffic from the public internet to flow into and out your VPC, you must attach what is called an internet gateway to your VPC.

**`AWS Direct Connect`** is a cloud service that makes it easy to establish a dedicated network connection from your on-premises infrastructure to AWS, providing the bandwitdth for large amounts of data transfer.

**`AWS Global Accelerator`** is a networking service that improves the availability and performance of the applications with local or global users. It provides static IP addresses that act as a fixed entry point to your application endpoints in AWS, such as `EC2` instances, `Elastic Load Balancers`, or `S3` buckets.

## Data analytics

### Services

For data analytics, these are the main services in AWS:

- **`Amazon Athena`**: It query data in S3 using SQL and it is a serverless service.
- **`Amazon Redshift`**: It is a fully managed data warehouse that makes it simple and cost-effective to analyze all your data using standard SQL and your existing Business Intelligence (BI) tools.
- **`Amazon Kinesis`**: It is a platform for streaming data on AWS, offering powerful services to make it easy to load and analyze streaming data, and also providing the ability to build custom streaming applications for specialized needs.
- **`AWS Glue`**: It is a fully managed extract, transform, and load (ETL) service that makes it easy for customers to prepare and load their data for analytics.

---

## Metrics and Monitoring

### Understand AWS Cloud Security, Governance, and Compliance Concepts

These services can help users to guarantee security, governance, and compliance in AWS cloud:

- **`Amazon CloudWatch`**: A monitoring and observability service. With CloudWatch dashboards you can create and visualize your metrics and get notified about changes in your AWS resources;
- **`AWS CloudTrail`**: A service that manages and monitors resources on AWS. For example, if you want to know who deleted a MongoDB instance, you can use `CloudTrail` to find out who deleted it and when. It provides a **CloudTrail Events** which is record significant activities in an AWS account and **CloudTrail Logs** for monitoring API activities for an AWS account;
- **`AWS Config`**: A service that enables you to assess, audit, and evaluate the configurations and evaluates them against the configurations you want to implement of your AWS resources;
- **`AWS Audit Manager`**: It is a service that continually audits your AWS usage to simplify risk and compliance assessments. It helps collect evidence and manage audit data;

If you want to enforce and manage rules across organizations and accounts for security, you can use **AWS Control Tower** which is a service to enforce
and manage governance rules for security, operations, and compliance at scale across all your organizations and accounts in AWS.

- **`AWS Service Catalog`**: It allows create, share and organize from a curated catalog of AWS resources. You can deploy baseline networking resources and
security tools for new AWS accounts or you can govern consistently across your organization.
- **`AWS Licensing Manager`**: It is a service that makes it easier to manage software licenses from vendors such as Microsoft, SAP, Oracle, and IBM across AWS and your on-premises environments.

---
