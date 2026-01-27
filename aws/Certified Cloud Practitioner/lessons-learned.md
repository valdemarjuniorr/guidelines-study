# Lessons Learned

Those lessons are annotations from practical exercises from [Whizlab AWS Certified Cloud Practitioner course](https://www.whizlabs.com/learn/course/aws-certified-cloud-practitioner/219).

## Domains

Those are the main domains for the questions and lessons learned. Those are annotations from right and wrong answers which are relevant to the
certification exam.

### Cloud Concepts

Two concepts design principles related to "Operational Excellence", pillar of the Well-Architected Framework are _Enable traceability_ and _Perform
operations as code_.

AWS Direct Connect establishes a dedicated, private network connection between your data center and AWS, ensure consistently high throughtpyt, low
jitter, and minimal latency. It does not use the public internet. Choose AWS Kinesis for real-time data ingestion, not for direct network connection.

### Cloud Technology and Services

AWS Compute Optimizer helps to identifying underutilized EC2 instances and right-sizing them, based on ML analyzing historical utilization
metrics(CPU, memory, network) and provides recommendations for the most cost-efficient compute options. If mention _machine learning-based analysis of
historical utilization metrics_ it's a hint to AWS Compute Optimizer.

To best integrate git-based hosting solution to integrate well with AWS services for CD/CI is use Github and integrate with AWS CodePipeline.

AWS CodeStar is a cloud-based service that helps in swift and quick development and building and deploying application in AWS.

For S3 self-created resources are only accessible to the user by default and server-side and client-side encryptions are supported by S3 for upload files.

To access S3 files temporarily can be provided using query string authentication.

Amazon Macie is a tool to protect data in S3 and not in EC2 instances.

AWS CodePipeline is a CD/CI service that automates the build, test, and deployment stages of your release process and it does not provision customer infrastructure itself. It can call other services like CloudFormation, Elastic Beanstalk or ECS.

AWS Application Discovery Service is helpful when organizations wants to gather information about on-premises servers and applications before migration to AWS.

AWS Device Farm is a testing services that lets you test mobile and web applications on real devices hosted in AWS. It supports both manual testing and automated testing frameworks.

Amazon Neptune is a fully managed graph database service optimized for storing and querying relationships between highly connected datasets.

Amazon QuickSight is fully managed BI service which enables to create and publish interactive dashboards with visualizations that are easy to explore.

Amazon S3 Transfer Acceleration is a feature designed to speed up file uploads and downloads between clients and S3 over long distances.

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

### Security and Compliance

When provisioning a security certificate from AWS Certificate Manager (ACM), a `CNAME` record would need to be created and the administrator would need
to acknowledge a verification email sent to an address of their choice.


### Billing, pricing and support

AWS Billing Conductor it helps to grouped and shown to each client, applying specific pricing models per client, and generate invoices based on those custom rates. It is ideal when offering services to resellers or business units who need tailored invoices.
