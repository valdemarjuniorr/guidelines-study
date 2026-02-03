# Lessons Learned

Those lessons are annotations from practical exercises from [Whizlab AWS Certified Cloud Practitioner course](https://www.whizlabs.com/learn/course/aws-certified-cloud-practitioner/219).

## Domains

Those are the main domains for the questions and lessons learned. Those are annotations from right and wrong answers which are relevant to the
certification exam.

### Cloud Concepts

Two concepts design principles related to "Operational Excellence", pillar of the Well-Architected Framework are _Enable traceability_ and _Perform
operations as code_.

AWS Direct Connect establishes a dedicated, private network connection between your data center and AWS, ensure consistently high throughput, low
jitter, and minimal latency. It does not use the public internet. Choose AWS Kinesis for real-time data ingestion, not for direct network connection.

AWS Professional Services is a global team of experts who work directly with enterprise customers to plan, implement and optimize complex cloud
solutions such as High Performance Computing (HPC) on AWS.

To enable AWS Trusted Advisor to automatically alerts via email whenever new detect an issue, you can configure directly in notifications settings in
the Trusted Advisor dashboard.

Amazon Elastic Block Store(EBS) are replicated within its AZ, but not across AZs. To achieve high availability across AZs, you must create snapshots
and manually replicate them to other AZs.

Amazon DynamoDB read consistency model to display the most accurate and up-to-date data is _Strongly Consistent_ reads. This is critical in real-time
systems like online games, where the players need to see accurate scores instantly after any update.

AWS Service Catalog helps organizations create and manage portfolios of pre-approved IT resources, such as a multi-tier application stack like web,
app, database and so on.

The AWS Cloud Adoption Framework (CAF) is guidance process to help with Business, People, Platform and Security.

### Cloud Technology and Services

AWS Compute Optimizer helps to identifying underutilized EC2 instances and right-sizing them, based on ML analyzing historical utilization
metrics(CPU, memory, network) and provides recommendations for the most cost-efficient compute options. If mention _machine learning-based analysis of
historical utilization metrics_ it's a hint to AWS Compute Optimizer.

To best integrate git-based hosting solution to integrate well with AWS services for CD/CI is use Github and integrate with AWS CodePipeline.

AWS CodeStar is a cloud-based service that helps in swift and quick development and building and deploying application in AWS.

For S3 self-created resources are only accessible to the user by default and server-side and client-side encryptions are supported by S3 for upload files.

To access S3 files temporarily can be provided using query string authentication.

Amazon Macie is a tool to protect data, like security and privacy using Machine Learning, in S3 and not in EC2 instances.

AWS CodePipeline is a CD/CI service that automates the build, test, and deployment stages of your release process and it does not provision customer infrastructure itself. It can call other services like CloudFormation, Elastic Beanstalk or ECS.

AWS Application Discovery Service is helpful when organizations wants to gather information about on-premises servers and applications before migration to AWS.

AWS Device Farm is a testing services that lets you test mobile and web applications on real devices hosted in AWS. It supports both manual testing and automated testing frameworks.

Amazon Neptune is a fully managed graph database service optimized for storing and querying relationships between highly connected datasets.

Amazon QuickSight is fully managed BI service which enables to create and publish interactive dashboards with visualizations that are easy to explore.

Amazon S3 Transfer Acceleration is a feature designed to speed up file uploads and downloads between clients and S3 over long distances or for teams
located across other countries.

_Multipart upload_ allows to upload large objects files as sets of parts, in parallel and reassemble them automatically at the destination on S3 bucket.

AWS CodeDeploy is designed for automating the deployment of applications across a variety of compute platforms as EC2 instances, on-premises servers, lambda functions and ECS services.

AWS AppSync enables developers to build scalable GraphQL APIs and real-time data using WebSockets and Pub/Sub messaging.

DynamoDB supports ACID operations.

AWS Global Acclelerator is suitable for applications that are non-HTTP/S such as VOIP, MQTT and gaming whereas CloudFront enhances the performance of
HTTP-based content such as dynamic web applications, images and videos.

AWS System Manager enables users to group AWS resources and view them based on application context, event across different Regions). It provides a unified operational dashboard for
automation, configuration management of cloud resources.

Amazon Dectective is purpose-built for deep investigation and root cause analysis of security incidents. It automatically coolects and correlates data
from multiple AWS services like CloudTrail, GuardDuty, VPC Flow Logs.

AWS IoT Greengrass is a solution for environments where intermittent connectivity and low-latency local response are critical. It extends AWS to edege devices so they can act locally on the data they generate.

AWS CloudHSM is a hardware-based security module that allows you to perform cryptographic operations like SSL/TLS oofloading directly on a dedicated
HSM cluster managed by AWS.

AWS Cognito User Pools is managed user directory that enables developers to add sign-up and sign-in features to web and mobile applications. AWS
Cognito Identity Polls is for authorization and not for authentication.

Amazon S3 Glacier console does not support uploading files directly. Files must be uploaded using AWS CLI, SDKs or third-party tools.

AWS Data Exchange is managed service for securely finding, subscribing to and exchanging datasets between AWS customers and data providers.

AWS DataSync allows automated, secure, online tranfers of large datasets from on-premises storage to AWS. The customer might have reliable internet
connection.

EC2 User Data scripts are scripts that runs during the instance launch process. You can update user data while the instance is running, as long as it uses an EBS root volume.

S3 Glacier Deep Archive is designed for long-term data archiving at the lowest storage cost among all AWS storage classes. Retrieval time is slower(up to 12-14 hours).

Amazon AppStream is designed to stream desktop applications to end-users via a browser, without needing to rewrite the application. It converts
traditional apps into SaaS easily, support high availability, scalability and integrates with user management systems like SAML 2.0.

AWS SageMaker is a fully managed service designed for building, training and deploying ML models it can helps dectecting fraud patterns in banking transactions for example. It allows: build ML models that learn patterns of normal vs suspicious activity, those models are real-time inference endpoints.

Amazon Kinesis Data Firehose it designed for loading streaming data into storage services like S3, Redshift or Elasticsearch.

Amazon LightSail is a virtual private server which can be used to quickly launch applications in AWS at a low cost. It can be used to launch simple web sites and set up a test environment.

### Security and Compliance

When provisioning a security certificate from AWS Certificate Manager (ACM), a `CNAME` record would need to be created and the administrator would need
to acknowledge a verification email sent to an address of their choice.

AWS Network Firewall is a managed, stateful firewall that helps inspect and filter VPC traffic enabling to deploy essential network protections for
your VPCs.

The best way to grant appropriate permissions to EC2 interact with S3 bucket, without hardcoding credentials, is using IAM roles. When you assign an
IAM role to an EC2, the instance automatically receives temporary security credentials to access AWS resources, as S3. The order do give permissions
is: Creating an IAM policy with the required permissions, creating an IAM role and attaching the policy to the role, and finally assigning the role to
the EC2 instance.

### Billing, pricing and support

AWS Billing Conductor it helps to grouped and shown to each client, applying specific pricing models per client, and generate invoices based on those custom rates. It is ideal when offering services to resellers or business units who need tailored invoices.

EC2 Dedicated hosts provides access to physical server where your EC2 instances run. This includes visibility into sockets, core and host-level
placement. This is critical for licensing models that are tied to physical serve.

AWS Prescriptive Guidance provides detailed and proven methods for cloud migration, modernization and cost optimization, offering playbooks,
architectural patterns and technical guides created by AWS experts and partners.
