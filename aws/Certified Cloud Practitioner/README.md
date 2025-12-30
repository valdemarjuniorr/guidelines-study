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
- Opeartional excellence;
- Cost optimization;
- Relaiability;
- Security;
- Susteinability;
- Performance efficiency;


