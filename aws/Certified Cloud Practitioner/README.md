# AWS Certified Cloud Practitioner

## The benefits of AWS Cloud

What is cloud computing?
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
- Rehost: Migrating to AWS server without making any changes;
- Relocate;
- Repurchase;
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
