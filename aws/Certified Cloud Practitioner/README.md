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

### The 7Rs Migration Strategies

The 7Rs are seven migration strategies to the cloud:

- **Retire**: Decommissioning servers that are no longer needed, saving upfront costs and ongoing costs
- **Retain**: Keep the server without migrating to AWS cloud
- **Rehost**: Migrating to AWS server without making any changes. Also known as "lift and shift"
- **Relocate**: For a large number of servers that are made up of one or more applications
- **Repurchase**: For applications with a different version or product and provides more value than the existing infrastructure. Also known as "drop and shop"
- **Replatform**: Move to server to AWS cloud and make changes to optimize the server
- **Refactor or Well-Architect**: Complete redesign and refactoring

For migration of low latency applications to access files, the recommended service would be `Amazon EFS` (file storage) and `Amazon RDS` (Relational database).

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
- **Labor costs**: Staffing for an on-premises environment or data centers, such as the network operation center technicians to manage the infrastructure of the servers
- **Software licensing costs**

---

## Security and Compliance

### Statement Descriptions

These are the 4 statements for the Security and Compliance domain:

- Understand the AWS shared responsibility model
- Understand AWS cloud security, governance, and compliance concepts
- Identify AWS access management capabilities
- Identify components and resources for security

---

### Understand the AWS Shared Responsibility Model

AWS is responsible for the security **of** the cloud, and the client is responsible for the data, permissions to each service, and the applications in the cloud.

---

### Understand AWS Cloud Security, Governance, and Compliance Concepts

These services can help users to guarantee security, governance, and compliance in AWS cloud:

- **`Amazon CloudWatch`**: A monitoring and observability service
- **`AWS CloudTrail`**: A service that manages and monitors resources on AWS. For example, if you want to know who deleted a MongoDB instance, you can use `CloudTrail` to find out who deleted it and when
- **`AWS Config`**: A service that enables you to assess, audit, and evaluate the configurations of your AWS resources

---

### Identify AWS Access Management Capabilities

**How is the root account in AWS different from IAM users?**

The root account has full access to all AWS services and resources in the account. `IAM` users have only the permissions that are granted to them by the root account or by other `IAM` users with appropriate permissions.

#### AWS IAM Features

- **IAM users**: Create users in `IAM` to provide access to AWS services and resources
- **IAM groups**: Create groups in `IAM` to manage permissions for multiple users
- **IAM roles**: Create roles in `IAM` to delegate access to AWS services and resources
- **IAM policies**: Create policies in `IAM` to define permissions for users, groups, and roles
- **IAM integrations**: `IAM` integrates with other AWS services to provide access control for those services

**When is it preferable to use IAM roles instead of IAM users?**

`IAM` roles are preferable when you want to delegate access to AWS services and resources without sharing long-term credentials. For example, when you want to grant access to an `EC2` instance to access `S3` buckets, you can use an `IAM` role instead of creating an `IAM` user with access keys.

---

### Identify Components and Resources for Security

**The differences between Network Access Control Lists (ACLs) and Security Groups:**

- **Network ACLs**: Associated with the subnet, not with the resources. They only manage traffic that crosses the subnet boundary. They are stateless, which means they only see traffic going in one direction. If you want more directional control, you need to create rules for both inbound and outbound traffic
- **Security Groups**: Associated with the resources, not with the subnet. They manage traffic for the resources. They are stateful, which means that inbound and outbound traffic are automatically allowed

#### AWS Security Services

- **`AWS WAF`**: Helps to control traffic with rules that you define that block common attack patterns such as SQL injections or cross-site scripting
- **`AWS Trusted Advisor`**
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

Database as a service where the user doesn't need to manage the database software or hardware.

### Amazon Aurora

A relational database engine that combines the speed and availability of high-end commercial databases with the simplicity and cost-effectiveness of open-source databases such as PostgreSQL and MySQL. The main benefit of `Amazon Aurora` over `Amazon RDS` is that Aurora shares cluster storage volume and not local storage.

### Amazon DynamoDB

A key-value and document database that delivers single-digit millisecond performance. It is not a relational database. It supports scale-out architecture automatically.

#### In-Memory Database Services

`Amazon ElastiCache` and `Amazon DynamoDB Accelerator (DAX)` are the main services for in-memory databases. They are used to improve the performance of web applications by retrieving data from high throughput and low latency in-memory data stores.

### Amazon Redshift

A fully managed data warehouse that makes it simple and cost-effective to analyze all your data using standard SQL and your existing Business Intelligence (BI) tools. It is used for online analytical processing (OLAP) and big data applications. It is based on PostgreSQL, but don't use it for transactional databases.

---

### Database Migration Tools

These are the migration tools available in AWS:

- **`AWS Snow Family`**: A collection of services to help users migrate large amounts of data to AWS cloud. The main services are Snowcone, Snowball, and Snowmobile.
- **`AWS Database Migration Service (DMS)`**: Manages database migration and schema conversion. This replication process is very admin intensive. The user creates a source and a target endpoint (replica), and DMS manages the replication process.
- **`AWS Schema Conversion Tool (SCT)`**: Used to convert the database schema from one database engine to another. For example, from Oracle to `Amazon Aurora`.
- **`AWS DataSync`**: Used to automate and accelerate moving data between on-premises storage and AWS storage services such as `S3`, `EFS`, and `FSx for Windows File Server`.

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

- **`Amazon EFS`** and **`Amazon FSx`**: Ideal for use cases like large content repositories, development environments, media stores, and home directories. `EFS` is used for Linux distributions. It is not allowed to use `EFS` for Windows; instead, use `FSx for Windows File Server`. `Lustre` is used for high-performance computing (HPC) and machine learning (ML) workloads that require fast storage with high levels of throughput and IOPS.

#### Block Storage

- **`Amazon EBS`** and **Instance Store**: Very resilient and is separate from the instance hardware. It is recommended for most system boot volumes.

---

## AWS Artificial Intelligence (AI) and Machine Learning (ML) Services

For ML, there are these services:

### Artificial Intelligence (AI) Services

These services provide pre-trained AI models that are ready to use for developers with no ML expertise. The main services are `Amazon Rekognition`, `Amazon Polly`, `Amazon Lex`, `Amazon Comprehend`, and `Amazon Transcribe`.

### Machine Learning (ML) Services

These services provide a platform for developers and data scientists to build, train, and deploy ML models. The main services are `Amazon SageMaker`, `AWS Deep Learning AMIs`, `AWS DeepRacer`, and `AWS DeepLens`.

### ML Frameworks and Infrastructure

These services provide a platform for developers and data scientists to build, train, and deploy ML models using popular ML frameworks. The main services are TensorFlow, PyTorch, Apache MXNet, Chainer, and Keras.

---

## Identify Services from Other In-Scope AWS Service Categories

### Event-Driven Services

- **`Amazon EventBridge`**: A serverless event bus that makes it easy to connect applications using data from your own applications, integrated Software-as-a-Service (SaaS) applications, and AWS services. EventBridge delivers a stream of real-time data from event sources, such as Zendesk, Datadog, or PagerDuty, and routes that data to targets like `AWS Lambda`.

### Customer Service and Engagement

- **`Amazon Connect`**: An easy-to-use omnichannel cloud contact center that helps companies provide superior customer service at a lower cost. With `Amazon Connect`, you can set up a contact center in just a few clicks and start providing better service to your customers.
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

### Compare AWS Pricing Models

Cost optimization has the ability to run systems to deliver business value at the lowest price point. There are some services to help users optimize costs in AWS:

- **`AWS Budgets`**: Used to set custom cost and usage budgets that alert you when you exceed your thresholds.
- **`AWS Cost and Usage Report`**: Used to create detailed reports about your AWS costs and usage.

AWS also provides cost-effective resources like Spot instances, Reserved instances, and cost-effective storage like `Amazon S3 Glacier` and `S3 Glacier Archive`.

---

### AWS Cost Optimization

- **Right sizing**: The process of matching instance types and sizes to your workload requirements to optimize performance and cost.
- **Increasing elasticity**: The process of using `Auto Scaling` to automatically adjust capacity to maintain steady, predictable performance at the lowest possible cost.
- **Choose the right pricing model**: The process of selecting the most cost-effective pricing model for your workloads, such as On-Demand, Reserved, or Spot Instances. Spot instances are the cheapest option, but they can be interrupted by AWS with a two-minute warning when AWS needs the capacity back.

---

### Pillars of Cost Optimization

- Right-sizing
- Match storage to usage
- Data transfer
- Measure, monitor, and improve

---

### Billing, Budgets, and Cost Management

- **`AWS Cost Explorer`**: A tool that enables you to view and analyze your AWS costs and usage. It provides detailed reports that can help you identify cost-saving opportunities and optimize your AWS spending.
- **`AWS Cost and Usage Report`**: A tool that provides detailed information about your AWS costs and usage. It allows you to create custom reports that can help you understand your spending patterns and identify areas for cost optimization.
- **`AWS Billing Conductor`**: A tool that helps you manage your AWS billing and payments. It provides features such as consolidated billing, cost allocation tags, and payment methods to help you streamline your billing processes and optimize your AWS spending.

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


