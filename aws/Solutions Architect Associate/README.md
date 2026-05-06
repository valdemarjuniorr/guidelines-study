# AWS Certified Solutions Architect - Associate (SAA-C03)

Those annotations are from [Whizlabs course](https://www.whizlabs.com/learn/course/aws-solutions-architect-associate/153) and from [AWS Course](https://skillbuilder.aws/category/exam-prep/solutions-architect-associate-SAA-C03).

## Overview

**The Main Pillars of the AWS Well-Architected Framework:**
- Operational excellence
- Cost optimization
- Reliability
- Security
- Sustainability
- Performance efficiency

## Design Secure Architectures (Domain 1)

### Design Secure Access to AWS Resources

You should know how to do the following:
- Apply AWS security best practices to AIM users and root users
- Design a flexible authorization model that includes IAM users, groups, roles and policies
- Design a role-based access control strategy
- Design a security strategy for multiple AWS accounts
- Determine the appropriate use of resource policies for AWS services
- Determine when to federate a directory service with IAM roles

What is a policy? It is a object that when associated with an identity or resource, define their permissions. There are two types of policies:
- `Identity-based policies`: These policies are attached to an IAM identity (user, group, or role) and define what actions that identity can perform on which AWS resources.
- `Bucket policies`: These policies are attached to an S3 bucket and define what actions can be performed on the bucket and its objects, and by whom.

### Design Secure Workloads and Application

There are two types of Amazon VPC, `default` e `custom`. The default VPC is automatically created in each AWS region and comes with a default subnet in each AZ. The custom VPC allows you to create your own network topology, including subnets, route tables, and security groups.

What is a subnet? It is where our services sit and run from inside our Amazon VPCs. They help to add structure and functionality to our VPCs. Subnets are an AZ resilient feature of AWS.

What is an endpoint service? They are gateway objects that we can create inside our VPC to connect to AWS public services without the need of a gateway like the internet gateway or the NAT gateway.

### Determine Appropriate Data Security Controls

In this section whether the data is in transit or at rest, it security needs to be evaluated. For the exam, you should know there are two types of encryption:
- At-rest encryption: This type of encryption protects data when it is stored on disk. AWS services that support at-rest encryption include Amazon S3, Amazon EBS, and Amazon RDS.
- At-transit encryption: This type of encryption protects data when it is transmitted over a network.

## Design Resilient Architectures (Domain 2)

Scaling is the ability to increase or decrease the capacity of a system based on demand. There are two types of scaling:
- `Horizontal scaling`: This type of scaling involves adding more instances to a system to increase its capacity. For example, adding more EC2 instances to a load balancer.
- `Vertical scaling`: This type of scaling involves increasing the resources of an existing instance to increase its

Elasticity is the ability of a system to automatically scale up or down based on demand.

### Design scalable and loosely coupled architectures


### Design of highly available and/or fault-tolerant architectures

For the exam, you should know about:
- `High availability`: It means designing for minimal downtime.
- `Fault tolerance`: It means designing for zero downtime.
- `Disaster recovery`: It means designing for recovery from a disaster.

For Disaster recovery objectives, you should know about the following strategies:
- `Recovery Point Objective(RPO)`: It is the maximum acceptable amount of time since the last data recovery point. Backups are taken every so many hours:minutes:seconds based on requirements.
- `Recovery Time Objective(RTO)`: It is the maximum acceptable delay between the interruption of service and restoration of service measured in hours:minutes:seconds based on requirements.

![DR strategies: Multi-site active/active](assets/fig1-dr-strategies.png)

## Design High-Performing Architectures (Domain 3)

### Determine high-performing and/or scalable storage solutions

In AWS, storage is available in three forms:
- `Object storage`: It is a type of storage that stores data as objects. Amazon S3 is an example of object storage.
- `Block storage`: It is a type of storage that stores data as blocks. Amazon EBS. It will scale automatically as the amount of data stored increases, up to a maximum of 16 TB per volume.
- `File storage`: It is a type of storage that stores data as files. Amazon EFS is an example of file storage.

What level of resiliency is S3? It is a globally resilient service and it ran in every AWS Region.

### Design high-performing and elastic compute solutions
In AWS, compute is available in three forms:
- `Intances`:
- `Containers`:
- `Functions`:

### Determine high-performing database solutions

Aurora is very different from RDS. Aurora uses the base architecture of a cluster. It is a cluster made up of a single primary instance and then zero or more replicas and Aurora has global database that can span multiple AWS regions.

RDS Proxy maintains a pool of established connections to your RDS instances. This reduce the stress on your compute and memory resources and support a large number and frequency of connections to help your application to scale.

### Determine high-performing and/or scalable network architectures
### Determine high-performing data ingestion and transformation solutions


## Design Cost-Optimized Architectures (Domain 4)

### Design cost-optimized storage solutions

### Design cost-optimized compute solutions
### Design cost-optimized database solutions
### Design cost-optimized network architectures


## Whizlabs Course

### Compute

For EC2 instances, there are instance families include general purpose, compute, optimized, memory optimized and storage optimized. The EC2 instances are represented by a letter and a number. The letter represents the instance family and the number represents the generation of the instance. For example, `t3` is a general purpose instance of the third generation.

#### Purchasing Options, Saving Plans and Tenancy models

There are some purchasing options for EC2 instances:
- `On-Demand`: You pay for compute capacity by the hour or second (depending on which instances you run) with no long-term commitments. This option is best for users that want the flexibility to use EC2 instances without any upfront payment or long-term commitment.
- `Reserved`: You can reserve an EC2 instance for a one-year or three-year term and receive a significant discount compared to On-Demand pricing. This option is best for users that have predictable workloads and can commit to using EC2 instances for a long period of time.
- `Spot Instances`: You can bid on unused EC2 capacity and run those instances for as long as your bid exceeds the current Spot price. This option is best for users that have flexible workloads and can tolerate interruptions.

##### Saving Plans

Those are the advantages of Saving Plans:
- Flexible pricing model that allows users to save up to 72% on their compute usage.
- Applies to EC2, Fargate and Lambda.
- Provide users with a discounted hourly rate in exchange for a commitment to use a specific amount of compute usage over a term of one or three years.
- Flexibility of moving compute usage across different instance families, sizes and regions within the same instance type.
- Saving Plans give you the flexibility to use the compute option that best suits your needs at low prices, without having to perform exchanges or modifications.

##### Tenancy models

There are three tenancy models for EC2 instances:
- `Shared tenancy`: This is the default tenancy model for EC2 instances. In this model, your EC2 instances run on shared hardware with other AWS customers.
- `Dedicated tenancy`: In this model, your EC2 instances run on hardware that is dedicated to you. This means that your instances will not share hardware with other AWS customers.
- `Dedicated Instances`: In this model, your EC2 instances run on hardware that is dedicated to you, but they are not physically isolated from other AWS customers. This means that your instances may share hardware with other AWS customers, but they will not share the same physical server.

#### EC2 Encryption

EBS encryption uses KMS keys when creating encrypted volumes and snapshots; Encrypts volume with a data key using the industry-standard AES-256 algorithm and it happens on the servers securing data-at-rest and data-in-transit between an instance and its attached EBS storage. You can encrypt the boot and the data volume of an EC2 instance.

#### EC2 Placement Groups

EC2 placement groups are a logical grouping of instances within a single Availability Zone. They are used to optimize the network performance of your instances. There are three types of placement groups:
- `Cluster`: It is recommended for applications that require low latency and high throughput.
- `Partition`: It is recommended for applications that require high availability and fault tolerance.
- `Spread`: It is recommended for applications that require high availability and fault tolerance.

All those types of placement groups are used to optimize the network performance of your instances.

Which are the rules and limitations of placement groups?
- You can create a maximum of 500 placement groups per account in each region.
- The name of the placement group must be unique within the region.
- Placement groups can not be merged.
- An instance can be launched in one placement group at a time; It can not span multiple placement groups.
- Can't launch Dedicated Hosts, a Spot instance that is configured to stop or hibernate or interruption in placement groups.
- It enables instances to utilize up to 10 Gbps for single-flow traffic, while instances outside of a cluster placement group have a limit of 5 Gbps for single-flow traffic.
- Launching multiple instance types in a cluster placement group reduces the likelihood of finding the necessary capacity for a successful launch, so it is recommended to use the same instance type for all instances int he group.

For sharing placement groups:
- You can share it across multiple AWS accounts or within your AWS Organization.
- You can not share it that has been shared with you.
- When you share a partition or spread placement group, the placement group limits do not change.
- To share in your AWS Organization, you must enable sharing with AWS Organizations.
- You are responsible for managing the instances owned by you in a shared placement group.
- You can not modify instances and capacity reservations that are associated with a shared placement group but not owned by you.
