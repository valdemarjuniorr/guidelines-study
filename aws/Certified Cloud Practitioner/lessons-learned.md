# Lessons Learned

Those lessons are annotations from practical exercises from [Whizlab AWS Certified Cloud Practitioner course](https://www.whizlabs.com/learn/course/aws-certified-cloud-practitioner/219).

## Domains

Those are the main domains for the questions and lessons learned. Those are annotations from right and wrong answers which are relevant to the
certification exam.

### Cloud Concepts
Two concepts design principles related to "Operational Excellence", pillar of the Well-Architected Framework are _Enable traceability_ and _Perform
operations as code_.

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

### Security and Compliance

When provisioning a security certificate from AWS Certificate Manager (ACM), a `CNAME` record would need to be created and the administrator would need
to acknowledge a verification email sent to an address of their choice.
