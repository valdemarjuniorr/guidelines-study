# Lessons Learned

These lessons are annotations from practical exercises from [Whizlabs AWS Certified Cloud Practitioner course](https://www.whizlabs.com/learn/course/aws-certified-cloud-practitioner/219).

## Domains

These are the main domains for the questions and lessons learned. These are annotations from right and wrong answers which are relevant to the certification exam.

### Cloud Concepts

#### Well-Architected Framework

Two design principles related to "Operational Excellence" pillar of the Well-Architected Framework are _Enable traceability_ and _Perform operations as code_.

#### AWS Frameworks and Services

The **AWS Cloud Adoption Framework (CAF)** is a guidance process to help with Business, People, Platform and Security.

**AWS Professional Services** is a global team of experts who work directly with enterprise customers to plan, implement and optimize complex cloud solutions such as High Performance Computing (HPC) on AWS.

**AWS Service Catalog** helps organizations create and manage portfolios of pre-approved IT resources, such as a multi-tier application stack like web, app, database and so on.

**AWS Application Discovery Service** is helpful when organizations want to gather information about on-premises servers and applications before migration to AWS.

**AWS Prescriptive Guidance** provides detailed and proven methods for cloud migration, modernization and cost optimization, offering playbooks, architectural patterns and technical guides created by AWS experts and partners.

### Cloud Technology and Services

#### Compute Services

**AWS Compute Optimizer** helps identify underutilized **EC2** instances and right-size them, based on ML analyzing historical utilization metrics (CPU, memory, network) and provides recommendations for the most cost-efficient compute options. If _machine learning-based analysis of historical utilization metrics_ is mentioned, it's a hint to **AWS Compute Optimizer**.

**AWS Compute Optimizer** uses ML to analyze historical utilization metrics (CPU, memory, network) and then recommends right-sizing **EC2** instances, Auto-Scaling groups, **EBS** volumes and **Lambda** functions. It helps reduce costs while improving performance.

**EC2** User Data scripts are scripts that run during the instance launch process. You can update user data while the instance is running, as long as it uses an **EBS** root volume.

**EC2 Dedicated Hosts** provides access to the physical server where your **EC2** instances run. This includes visibility into sockets, cores and host-level placement. This is critical for licensing models that are tied to physical servers.

**Amazon LightSail** is a virtual private server which can be used to quickly launch applications in AWS at a low cost. It can be used to launch simple websites and set up a test environment.

**AWS Batch** uses the _priority parameter of the job queue_ to determine the order in which jobs are considered for scheduling when multiple queues share the same compute resources. A higher numerical priority value means that queue's jobs are evaluated first.

**AWS Lambda** functions can be optimized using **AWS Compute Optimizer** recommendations.

#### Storage Services

**Amazon Elastic Block Store (EBS)** volumes are replicated within its AZ, but not across AZs. To achieve high availability across AZs, you must create snapshots and manually replicate them to other AZs.

**Amazon EBS** volumes store their backups as snapshots in **Amazon S3**, but the volumes themselves are not stored in **S3**.

**Amazon S3** self-created resources are only accessible to the user by default and server-side and client-side encryptions are supported for uploading files.

To access **S3** files temporarily can be provided using query string authentication.

To enable **S3** replication, it is not necessary that the bucket owner of the destination must have both source and destination AWS regions enabled for their account. Only the source bucket owner needs access to both regions, as replication and control are handled from the source side.

**Amazon S3 Transfer Acceleration** is a feature designed to speed up file uploads and downloads between clients and **S3** over long distances or for teams located across different countries.

_Multipart upload_ allows you to upload large object files as sets of parts, in parallel and reassemble them automatically at the destination on **S3** bucket.

**Amazon S3 Glacier** console does not support uploading files directly. Files must be uploaded using **AWS CLI**, SDKs or third-party tools.

**S3 Glacier Deep Archive** is designed for long-term data archiving at the lowest storage cost among all AWS storage classes. Retrieval time is slower (up to 12-14 hours).

**Amazon EFS** is a serverless, fully managed, POSIX-compliant file system that clients mount using NFSv4/v4.1 protocol, suitable for many Linux workloads and can be accessed from **EC2** and on-premises via **VPN**/**Direct Connect**.

With **Amazon EFS** you can store media assets that can be accessed and processed in real-time and to achieve sub-millisecond latencies it is necessary to configure **EFS** One Zone storage class with General Purpose performance mode. The Max I/O performance mode is only available with Standard storage class. One Zone always uses General Purpose mode by design.

**Amazon FSx for Lustre** is a POSIX-compliant, high-performance parallel file system for Linux/HPC workloads, also mounted for Linux clients and commonly linked with **S3**.

#### Database Services

**Amazon DynamoDB** read consistency model to display the most accurate and up-to-date data is _Strongly Consistent_ reads. This is critical in real-time systems like online games, where players need to see accurate scores instantly after any update.

By default, **DynamoDB** reads are eventually consistent which may, very briefly, return a stale value immediately after a successful write. If you need the latest value right after an update in the same region, set the read to strongly consistent.

**DynamoDB** supports ACID operations.

**Amazon Aurora** scales up to 128 TB and it is fully managed by **Amazon RDS**, handling backups, patching and failover automatically.

**Amazon Neptune** is a fully managed graph database service optimized for storing and querying relationships between highly connected datasets.

#### Networking Services

**AWS Direct Connect** establishes a dedicated, private network connection between your data center and AWS, ensuring consistently high throughput, low jitter, and minimal latency. It does not use the public internet. Choose **AWS Kinesis** for real-time data ingestion, not for direct network connection.

**AWS Site-to-Site VPN** creates a secure, encrypted tunnel over the public internet between your on-premises network and your VPC. This allows private data transmission and is a common and cost-effective way for enterprises to establish hybrid cloud connectivity.

**Elastic Network Interfaces (ENI)** is a virtual network interface adapter that you can attach to **EC2** instances in your VPC.

**AWS Transit Gateway** acts as a hub that interconnects your VPCs and your on-premises network through a single gateway, instead of managing complex peering relationships between each VPC and the on-premises data center.

**Customer Gateway (CGW)** represents the customer's end of the VPN connection. It is the on-premises VPN device that the customer configures to establish an IPsec VPN tunnel with AWS.

**VPC Peering** allows you to connect two VPCs, even in different regions, using AWS' private global network, without traversing the public internet, and without requiring a VPN or hardware device. It is cost-effective and simple for point-to-point communication between two VPCs.

The default number of Network ACLs you can create per VPC is 200, regardless of how many AZs the VPC spans. You can request an increase through a Service Quota request. Network ACLs limits apply at the VPC level, not per AZ.

**AWS Global Accelerator** is suitable for applications that are non-HTTP/S such as VOIP, MQTT and gaming whereas **CloudFront** enhances the performance of HTTP-based content such as dynamic web applications, images and videos.

#### Developer Tools and CI/CD

To best integrate a git-based hosting solution with AWS services for CI/CD is to use GitHub and integrate with **AWS CodePipeline**.

**AWS CodeStar** is a cloud-based service that helps in swift and quick development and building and deploying applications in AWS.

**AWS CodePipeline** is a CI/CD service that automates the build, test, and deployment stages of your release process and it does not provision customer infrastructure itself. It can call other services like **CloudFormation**, **Elastic Beanstalk** or **ECS**.

**AWS CodeDeploy** is designed for automating the deployment of applications across a variety of compute platforms as **EC2** instances, on-premises servers, **Lambda** functions and **ECS** services.

#### Data and Analytics Services

**Amazon Kinesis Data Firehose** is designed for loading streaming data into storage services like **S3**, **Redshift** or **Elasticsearch**.

**Amazon QuickSight** is a fully managed BI service which enables you to create and publish interactive dashboards with visualizations that are easy to explore.

**AWS Data Exchange** is a managed service for securely finding, subscribing to and exchanging datasets between AWS customers and data providers.

**AWS DataSync** allows automated, secure, online transfers of large datasets from on-premises storage to AWS. The customer must have a reliable internet connection.

**Amazon OpenSearch Service** supports vector search using the k-NN (k-Nearest Neighbors) plugin, allowing you to store high-dimensional vector embeddings and perform similarity search queries.

#### Machine Learning and AI Services

**AWS SageMaker** is a fully managed service designed for building, training and deploying ML models. It can help detect fraud patterns in banking transactions for example. It allows you to build ML models that learn patterns of normal vs suspicious activity, and these models are real-time inference endpoints.

**AWS Lex** is designed for building chatbots and conversational interfaces using voice and text. It uses Automatic Speech Recognition (ASR) and natural language understanding (NLU) to interpret user intent and respond appropriately.

**AWS Polly** is a text-to-speech service that converts text into realistic voice.

**AWS Kendra** is a search service that helps retrieve answers from documents using NLP (Natural Language Processing).

#### Application Services

**AWS AppSync** enables developers to build scalable GraphQL APIs and real-time data using WebSockets and Pub/Sub messaging.

**Amazon AppStream** is designed to stream desktop applications to end-users via a browser, without needing to rewrite the application. It converts traditional apps into SaaS easily, supports high availability, scalability and integrates with user management systems like SAML 2.0.

#### IoT Services

**AWS IoT Core** uses the MQTT (Message Queuing Telemetry Transport) protocol which uses low bandwidth, handles spotty network conditions, and works well for devices with limited power and memory.

**AWS IoT Greengrass** is a solution for environments where intermittent connectivity and low-latency local response are critical. It extends AWS to edge devices so they can act locally on the data they generate.

#### Monitoring and Management Services

To enable **AWS Trusted Advisor** to automatically send alerts via email whenever it detects a new issue, you can configure it directly in the notifications settings in the **Trusted Advisor** dashboard.

To receive **AWS Trusted Advisor** notifications, you need to set it up from the dashboard by providing a list of recipients and selecting resource items for which status is required.

**AWS Systems Manager** enables users to group AWS resources and view them based on application context, even across different Regions. It provides a unified operational dashboard for automation and configuration management of cloud resources.

#### Testing Services

**AWS Device Farm** is a testing service that lets you test mobile and web applications on real devices hosted in AWS. It supports both manual testing and automated testing frameworks.

### Security and Compliance

#### Identity and Access Management

The best way to grant appropriate permissions to **EC2** to interact with **S3** bucket, without hardcoding credentials, is using IAM roles. When you assign an IAM role to an **EC2**, the instance automatically receives temporary security credentials to access AWS resources, such as **S3**. The order to give permissions is: Creating an IAM policy with the required permissions, creating an IAM role and attaching the policy to the role, and finally assigning the role to the **EC2** instance.

To share consistent permissions across several accounts by reusing an IAM policy from one account to another, you can use IAM roles and trust policies for cross-account access.

**IAM Identity Center** provides centralized access management across multiple AWS accounts and integrates with external identity providers (e.g.: Azure AD, Okta). It supports SSO, user/group-based permissions, and automated provisioning. It is ideal when you need to manage access to both AWS accounts and third-party applications from a single location.

**AWS IAM Access Analyzer** is designed to help you analyze permissions granted using IAM policies. It uses logic-based reasoning to determine what resources are shared with external entities and offers clear, actionable recommendations to help reduce broad or unintended access.

**AWS Systems Manager Session Manager** is a secure and interactive shell and CLI access tool for **EC2**. It lets you connect to your instances without opening port 22 (SSH), managing or rotating SSH keys and needing a bastion host.

**Security Token Service (STS)** with Identity Federation is the best way to make mobile apps access resources like **S3** or **DynamoDB**, allowing a user to access resources within a session.

**AWS Cognito User Pools** is a managed user directory that enables developers to add sign-up and sign-in features to web and mobile applications. **AWS Cognito Identity Pools** is for authorization and not for authentication.

#### Security Services

When provisioning a security certificate from **AWS Certificate Manager (ACM)**, a `CNAME` record would need to be created and the administrator would need to acknowledge a verification email sent to an address of their choice.

**AWS Network Firewall** is a managed, stateful firewall that helps inspect and filter VPC traffic, enabling you to deploy essential network protections for your VPCs.

**AWS WAF** can integrate with **CloudFront**, **Application Load Balancer (ALB)**, **API Gateway** and **AWS AppSync** to protect web applications from common web exploits and bots.

**Amazon Macie** is a tool to protect data, like security and privacy using Machine Learning, in **S3** and not in **EC2** instances.

**Amazon Detective** is purpose-built for deep investigation and root cause analysis of security incidents. It automatically collects and correlates data from multiple AWS services like **CloudTrail**, **GuardDuty**, VPC Flow Logs.

**AWS CloudHSM** is a hardware-based security module that allows you to perform cryptographic operations like SSL/TLS offloading directly on a dedicated HSM (Hardware Security Module) cluster managed by AWS.

**AWS Systems Manager Parameter Store** helps store plain-text or encrypted configuration values securely using **AWS KMS** integration. It is ideal for low-cost, lightweight secret storage. It is free for standard parameters.

### Billing, Pricing and Support

**AWS Billing Conductor** helps to group and show to each client, applying specific pricing models per client, and generate invoices based on those custom rates. It is ideal when offering services to resellers or business units who need tailored invoices.

The support plans that provide 24/7 access to technical support via phone, chat and email are **Business** and **Enterprise** support plans.

**Consolidated Billing** is a feature within **AWS Organizations** that enables a company to combine usage across multiple accounts into a single bill. Each single account retains its own services and resources, but costs are aggregated under a Management Account (main payer). This makes billing simpler and also provides cost tracking per individual account, ensuring full visibility.

**AWS Cost Anomaly Detection** uses ML to analyze your AWS spending patterns and automatically detect unusual charges. It sends alerts via email or **SNS** when anomalies are found.

A Master account remains free of any resources, but nothing stops the owner of the Master account from creating resources, for example, creating an **S3** bucket.
