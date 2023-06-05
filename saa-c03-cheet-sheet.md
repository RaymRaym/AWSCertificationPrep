## AWS Lambda Function

- CloudWatch Events EventBridge -> trigger every certain time -> AWS lambda function perofrom a task

- Limits

  Maximum timeout 15 min

  memory allocation : 128 MB - 10 GB

  Environment variables 4 KB

  disk capacity 512MB - 10 GB

- Lambda in VPC

  Lamdda will create an ENI(Elastic Network Interface) in your subnets

  Lambda with RDS Proxy

  **The Lambda function must be deployed in your VPC, because RDS Proxy is never pubilcly accessible.**

 

## Amazon Certificate Manager(ACM)

 To increase the application's performance, the solutions architect should import the SSL certificate into AWS Certificate Manager (ACM) and create an Application Load Balancer with an HTTPS listener that uses the SSL certificate from ACM. An Application Load Balancer (ALB) can offload the SSL termination process from the EC2 instances, which can help to increase the compute capacity available for the web application. By creating an ALB with an HTTPS listener and using the SSL certificate from ACM, the ALB can handle the SSL termination process, leaving the EC2 instances free to focus on running the web application.

## Amazon CloudWatch

- composite alarm

  The composite alarm goes into ALARM state **only if all conditions of the rule are met.**

## Amazon S3

S3 is the cheapest and most scalable.

- S3 Replication (cross region)

  - Unencrypted objects and objects encrypted with SSE-S3 are replicated by default

  - bjects encrypted with SSE-C(customer provided key) are never replicated
  - For objects encrypted with SSE-KMS, you need to enable the option(IAM Roles .....)

- **S3 can NOT send event notification to SageMaker.**

- S3 Transfer Acceleration

- S3 File Gateway

  ache recent access file

- S3 Lifecycle Policy

- s3:PutObjectLegalHold

  The Object Lock legal hold operation enables you to place a legal hold on an object version. Like setting a retention period, **a legal hold prevents an object version from being overwritten or deleted.** However, a legal hold doesn't have an associated retention period and remains in effect until removed.

- preassigned URL

  preassigned URL is for upload or download for temporary time and for specific users outside the company. signed URL is for temporary access

- S3 Object Lock enabled

  - Compliance Mode

    In compliance mode, a protected object version can't be overwritten or deleted by any user, including the root user in your AWS account. When an object is locked in compliance mode, its retention mode can't be changed, and its retention period can't be shortened.

    **Compliance mode helps ensure that an object version can't be overwritten or deleted for the duration of the retention period.**

  - Governance Mode

    In governance mode, users can't overwrite or delete an object version or alter its lock settings unless they have special permissions. With governance mode, you protect objects against being deleted by most users, but you can still grant some users permission to alter the retention settings or delete the object if necessary. 

    **In Governance mode, Objects can be deleted by some users with special permissions.**

## Amazon API Gateway

AWS Lambda + API Gateway ,support for the WebSocket Protocol, API versioning, different environments, security

## NAT Gateway

NAT Gateway will be created Public Subnet and Provide access to Private Subnet

## Amazon EC2

- Auto scaling groups can not span multi region

- **A target tracking policy** allows the Auto Scaling group to automatically adjust the number of EC2 instances in the group **based on a target value for a metric**.

## Amazon ECS

- AWS Fargate (serverless)

  AWS Fargate is a technology that you can use with Amazon ECS to run containers without having to manage servers or clusters of Amazon EC2 instances. With Fargate, you no longer have to provision, configure, or scale clusters of virtual machines to run containers. This removes the need to choose server types, decide when to scale your clusters, or optimize cluster packing. 

- To ensure that an Amazon Elastic Container Service (ECS) application has permission to access Amazon Simple Storage Service (S3), the correct solution is to create an AWS Identity and Access Management (IAM) role with the necessary S3 permissions and specify that role as the taskRoleArn(Amazon Resource Name) in the task definition for the ECS application. 

## AWS Backup

Using AWS Backup is a simple and efficient way to **backup EC2 instances and RDS databases to a separate region**. It requires **minimal operational overhead** and can be easily managed through the AWS Backup console or API. AWS Backup can also provide automated scheduling and retention management for backups, which can help ensure that backups are always available and up to date.

AWS Backup allows you to backup your S3 data stored in the following S3 Storage Classes: 

- S3 Standard 
- S3 Standard - Infrequently Access (IA) 
- S3 One Zone-IA 
- S3 Glacier Instant Retrieval
- S3 Intelligent-Tiering (S3 INT)

**Don't support Glacier Deep**

## AWS Transfer Family

For Exam : Whenever you see **SFTP , FTP** look for "Transfer" in options available.

AWS Transfer Family is a fully managed AWS service that you can use to **transfer files into and out of** **Amazon Simple Storage Service (Amazon S3) storage or Amazon Elastic File System (Amazon EFS)** file systems over the following protocols: Secure Shell (SSH) File Transfer Protocol (SFTP): version 3 File Transfer Protocol Secure (FTPS) File Transfer Protocol (FTP) Applicability Statement 2 (AS2)



## Amazon DataSync

To automate the process of transferring the data from the on-premises SFTP server to an EC2 instance with an EFS file system, you can use AWS DataSync. AWS DataSync is a fully managed data transfer service that simplifies, automates, and accelerates transferring data between on-premises storage systems and Amazon S3, Amazon EFS, or Amazon FSx for Windows File Server. To use AWS DataSync for this task, you should **first install an AWS DataSync agent in the on-premises data center**. This agent is a lightweight software application that you install on your on-premises data source. T**he agent communicates with the AWS DataSync service to transfer data between the data source and target locations.**

## Application Load Balancer

can do

- http - > https redirect rule with ACM

## Gateway Load balancer

Gateway Load Balancers enable you to deploy, scale, and **manage virtual appliances**, such as firewalls, **intrusion detection** and prevention systems, and **deep packet inspection** systems. It combines a transparent network gateway (that is, a single entry and exit point for all traffic) and distributes traffic while scaling your virtual appliances with the demand.

A Gateway Load Balancer **operates at the third layer of the Open Systems Interconnection (OSI) model,** the network layer. It listens for **all IP packets** across all ports and forwards traffic to the target group that's specified in the listener rule. It maintains stickiness of flows to a specific target appliance using 5-tuple (for TCP/UDP flows) or 3-tuple (for non-TCP/UDP flows). The Gateway Load Balancer and its registered virtual appliance instances exchange application traffic using the [GENEVE](https://datatracker.ietf.org/doc/html/rfc8926) protocol on port 6081

## Spot Fleet

spot fleet = spot Instances + on-demand 

## Amazon CloudFront

- CloudFront caches the static content. **It also accepts requests for dynamic content and forward it to the ALB via AWS backbone (very fast).**

- CloudFront offers several options for streaming your media to global viewers—**both pre-recorded files and live events.**

- Field-level Encrpytion

  Field-level encryption allows you to enable your users to securely upload sensitive information to your web servers. The sensitive information provided by your users is encrypted at the edge, close to the user, and remains encrypted throughout your entire application stack

- origin access identity (OAI)

  I want to restrict access to my Amazon Simple Storage Service (Amazon S3) bucket so that objects can be a**ccessed only through my Amazon CloudFront distribution**. How can I do that? Create a CloudFront origin access identity (OAI)

## AWS Global Accelerator

TCP / UDP

## Amazon MQ



## Amazon SQS

- Standard queue

- FIFO queue

- dead-letter queues(DLQ)

  Amazon SQS supports dead-letter queues (DLQ), which other queues (source queues) can target for messages that can't be processed (consumed) successfully.

## Amazon SNS(Simple Notification Service)

pub/sub messaging service, one-to-many communication

Amazon SNS defines a *delivery policy* for each delivery protocol. The delivery policy defines how Amazon SNS retries the delivery of messages when server-side errors occur (when the system that hosts the subscribed endpoint becomes unavailable). When the delivery policy is exhausted, Amazon SNS stops retrying the delivery and discards the message—unless a dead-letter queue is attached to the subscription. For more information,

**A dead-letter queue associated with an Amazon SNS subscription is an ordinary Amazon SQS queue.**

### Amazon Kinesis Data Firehose

a fully managed service for **streaming data to Amazon OpenSearch Service** (Amazon Elasticsearch Service) and other destinations. You can configure the log group as the source of the delivery stream and Amazon OpenSearch Service as the destination. This solution requires minimal operational overhead, as Kinesis Data Firehose automatically scales and handles data delivery, transformation, and indexing.



## Amazon Kinesis

Kinesis stream **save data for up to 24 hours**, doesn't meet the 2 day requirement. Kinesis streams **don't have fail-safe** for failed processing, unlike SQS.

## Amazon Athena

Athena helps you analyze unstructured, semi-structured, and structured data **stored in Amazon S3**. Examples include **CSV, JSON, or columnar data formats such as Apache Parquet and Apache ORC**. You can use Athena to run **ad-hoc queries** using ANSI SQL, without the need to aggregate or load the data into Athena.

## Amazon RedShift

## Amazon Glue

- AWS Glue tracks data that has already been processed during a previous run of an ETL job by persisting state information from the job run. This persisted state information is called a job bookmark. **Job bookmarks help AWS Glue maintain state information and prevent the reprocessing of old data.**

## AWS Snowball Edge 

​	On a Snowball Edge device you can copy files with a speed of up to 100Gbps. 70TB will take around 5600 seconds, so very quickly, less than 2 hours. The downside is that it'll take between 4-6 working days to receive the device and then another 2-3 working days to send it back and for AWS to move the data onto S3 once it reaches them. Total time: 6-9 working days. Bandwidth used: 0.

## Amazon Aurora

Aurora is a fully managed, MySQL-compatible relational database that is designed for high performance and high availability. Aurora Multi-AZ deployments **automatically maintain a synchronous standby replica in a different Availability Zone to provide high availability**. Additionally, Aurora Auto Scaling allows you to automatically scale the number of Aurora Replicas in response to read workloads, allowing you to meet the demand of unpredictable read workloads while maintaining high availability. This would provide an automated solution for scaling the database to meet the demand of the application while maintaining high availability.

The most cost-effective solution for **addressing high ReadIOPS and CPU utilization when running large reports would be to migrate the monthly reporting to an Aurora Replica**. An Aurora Replica is a read-only copy of an Aurora database that is updated in real-time with the primary database. By using an Aurora Replica for running large reports, the primary database will be relieved of the additional read load, improving performance for the ecommerce application

## Amazon QuickSight

QuickSight **don't support IAM. We use users and groups** to view the QuickSight dashboard

## Amazon Elastic Block Store (Amazon EBS)

- Snapshot

  **A snapshot is constrained to the AWS Region where it was created.** After you create a snapshot of an EBS volume, you can use it to create new volumes in the same Region. For more information, see [Create a volume from a snapshot](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-creating-volume.html#ebs-create-volume-from-snapshot). You can also **copy snapshots across Regions**, making it possible to use multiple Regions for geographical expansion , data center migration, and disaster recovery. You can copy any accessible snapshot that has a `completed` status. For more information, see [Copy an Amazon EBS snapshot](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-copy-snapshot.html).

- Fast Snapshot Restore(FSR)

  Amazon EBS fast snapshot restore (FSR) enables you to create a volume from a snapshot that is fully initialized at creation. This eliminates the latency of I/O operations on a block when it is accessed for the first time. Volumes that are created using fast snapshot restore instantly deliver all of their provisioned performance.

## Amazon RDS

- Storage Auto Scaling

  RDS Storage Auto Scaling automatically scales storage capacity in response to growing database workloads, with **zero downtime**.

- Amazon RDS Custom for Oracle

  Amazon RDS Custom is a managed database service for legacy, custom, and packaged applications that require access to the underlying operating system and database environment. Amazon RDS Custom automates setup, operation, and scaling of databases in the cloud while **granting customers access to the database and underlying operating system to configure settings, install patches, and enable native features to meet the dependent application's requirements**

  - **You can't create cross-Region RDS Custom for Oracle replicas.**

- Amazon RDS event notification 

  doesn't support any notification when data inside DB is updated/deleted/inserted. You can use a SQS to do notification.

- RDS Multi-AZ = Synchronous = Disaster Recovery (DR) 

- **Read Replica = Asynchronous**

- Amazon RDS Proxy

  Many applications, including those built on modern serverless architectures, can have **a large number of open connections** to the database server and may open and close database connections at a high rate, exhausting database memory and compute resources. Amazon RDS Proxy allows applications to pool and share connections established with the database, improving database efficiency and application scalability.
  
  **The Lambda function must be deployed in your VPC, because RDS Proxy is never pubilcly accessible.**

## Amazon DynamoDB

- highly available with replication across multiple AZs
- NoSQL databse with transaction suppport.
- standard / infrequent access tables 
- In DynamoDB, you can rapidly evolve schemas

- Amazon DynamoDB has two **read/write capacity** modes for processing reads and writes on your tables:

  1. Provisioned Mode (default)

     plan capacity beforehand

  2. On-demand Capacity (expensive)

     When you choose on-demand mode, DynamoDB instantly **accommodates your workloads** as they ramp up or down to any previously reached traffic level. If a workload’s traffic level hits a new peak, **DynamoDB adapts rapidly to accommodate the workload**. Tables that use on-demand mode deliver the same single-digit millisecond latency, service-level agreement (SLA) commitment, and security that DynamoDB already offers. You can choose on-demand for both new and existing tables and you can continue using the existing DynamoDB APIs without changing code.
  
     On-demand mode is a good option if any of the following are true:

     - You create new tables with unknown workloads.

     - You have **unpredictable** application traffic.
  
     - You prefer the ease of paying for only what you use.

- DAX (DynamoDB Accelarator)

  Amazon DynamoDB Accelerator (DAX) is a fully managed, highly available, **seamless in-memory cache for DynamoDB** that helps improve the read performance of DynamoDB tables. DAX provides a caching layer between the application and DynamoDB, reducing the number of read requests made directly to DynamoDB. This can significantly reduce read latencies and improve overall application performance.

- DynamoDB GLobal Tables

  enable DynamoDB Streams first

  two-way replication

  accessible with low latency in multiple-regions

- TTL

  automatically delete items after an expiry timestamp 

  use cases: web session handling

## Amazon Database Migration Service(DMS)

- Create an ongoing replication task: 

  An ongoing replication task can be used to **continuously replicate** data from the on-premises database to the Aurora database. This will ensure that the Aurora database remains in sync with the on-premises database.

## EFS

​	Concurrent or at the same time key word for EFS

## VPC

- Traffic Mirroring

  Traffic Mirroring is an Amazon VPC feature that you can use to copy network traffic from an elastic network interface of type `interface`. You can then send the traffic to out-of-band security and monitoring appliances for:

  - Content inspection
  - Threat monitoring
  - Troubleshooting

  The security and monitoring appliances can be deployed as individual instances, or as a fleet of instances behind either a Network Load Balancer or a Gateway Load Balancer with a UDP listener. Traffic Mirroring supports filters and packet truncation, so that you can extract only the traffic of interest, using the monitoring tools of your choice.

- VPC endpoint

  VPC endpoint allows you to connect to AWS services using a private network instead of using the public Internet

  A VPC endpoint enables private connectivity between the VPC and S3 without using an internet gateway or NAT device. 

## Amazon Rekognition

Amazon Rekognition makes it easy to add image and video analysis to your applications. You just provide an image or video to the Amazon Rekognition API, and the service can identify objects, people, text, scenes, and activities. It can detect any inappropriate content as well. Amazon Rekognition also provides highly accurate facial analysis and facial recognition. With Amazon Rekognition Custom Labels, you can create a machine learning model that finds the objects, scenes, and concepts that are specific to your business needs.

## Amazon Textract

Amazon Textract enables you to add document text detection and analysis to your applications. You provide a document image to the Amazon Textract API, and the service detects the document text. Amazon Textract works with formatted text and can detect words and lines of words that are located close to each other. It can also analyze a document for items such as related text, tables, key-value pairs, and selection elements.

## Amazon DocumentDB

MongoDB

## Amazon Transcribe

speech -> text

Amazon Transcribe is a service that **automatically transcribes spoken language into written text**. It can handle **multiple speakers** and can generate transcript files in real-time or asynchronously. These transcript files can be stored in Amazon S3 for long-term storage. 

## Amazon Cognito

To control access to the REST API and reduce development efforts, the company can use an **Amazon Cognito user pool authorizer in API Gateway**. This will allow Amazon Cognito to validate each request and ensure that only authenticated users can access the API. This solution has the **LEAST operational overhead**, as it does not require the company to develop and maintain any additional infrastructure or code.

## AWS Network Firewall

AWS Network Firewall is a managed firewall service that provides filtering for **both inbound and outbound network traffic**. It allows you to create rules for traffic **inspection and filtering**, which can help **protect your production VPC**.

## Amazon Lambda

Lambda is an event-driven, serverless compute service that automatically scales with the number of requests, making it more suitable for handling variable workloads and reducing response times during high traffic periods.

## Security / Access / Restriction

- IAM role

  Always remember that **you should associate IAM roles to EC2 instances**

- SCP (Service Control Policy)

  Service control policies (SCPs) are one type of policy that you can use to manage your organization. SCPs offer central control over the maximum available permissions for all accounts in your organization, allowing you to ensure your accounts stay within your organization's access control guidelines. 

## Elastic Beanstalk

Elastic Beanstalk is a fully managed service that makes it easy to deploy and run applications in the AWS; To enable frequent testing of new site features, you can use URL swapping to switch between multiple Elastic Beanstalk environments.

## AWS Certificate Manager(ACM)

Easily provision, manage, and deploy **TLS Certificates**

Integration with(Load TLS Certificates on)

- elastic load balancers
- CloudFront Distributions
- APIs on API Gateway

## AWS Secrets Manager

AWS Secrets Manager is a secrets management service that helps you protect access to your applications, services, and IT resources. This service enables you to rotate, manage, and retrieve database credentials, API keys, and other secrets throughout their lifecycle.

- You can rotate secrets on a schedule or on demand by using the Secrets Manager console, AWS SDK, or AWS CLI.
- rotation of secrets every X days
- **secrets are encrypted by KMS**
- With Secrets Manager, you can store, retrieve, manage, and rotate your secrets, including database credentials, API keys, and other secrets. When you create a secret using Secrets Manager, it’s created and managed in a Region of your choosing. Although scoping secrets to a Region is a security best practice, there are scenarios such as disaster recovery and **cross-Regional redundancy that require replication of secrets across Regions**. Secrets Manager now makes it possible for you to easily replicate your secrets to one or more Regions to support these scenarios

## AWS Systems Manager Parameter Store

secure storage for configuration and secrets

version tracing of them

notifications with EventBridge

serverless, scalable

no auto rotation for keys but TTL

Paremter is stored, and encrypted / decrypted by KMS

## AWS Key Management Service (AWS KMS)

- Able to audit KMS Key usage using CloudTrail

- Server-side encryption with AWS KMS keys (SSE-KMS)

  SSE-KMS allows you to use keys that are managed by the AWS Key Management Service (KMS) to encrypt your data at rest. KMS is a fully managed service that makes it easy to create and control the encryption keys used to encrypt your data. With automatic key rotation enabled, KMS will automatically create a new key for you on a regular basis, **every year**, and use it to encrypt your data. This simplifies the key rotation process and reduces the operational burden on your team.

  Imported KMS Key: only manual rotation possible using alias


- KMS Multi-Region Key

  Encrypt in one Region and decrypt in other Regions (DynamoDB Global Tables, Global Aurora)

- Copy Snapshots across regions

  KMS ReEncrypt with KMS Key B

- KMS key policy

  Default : complete access to the key to the root user = entrie  AWS account  

  cutome: Define users, roles and who can adminiter the key. Useful for cross-account access of the key 

- aws:PrincipalOrgID

  the condition key aws:PrincipalOrgID can prevent the members who don't belong to your organization to access the resource

## AWS Config

Configuration changes= AWS Config

AWS Config provides a detailed view of the resources associated with your AWS account, including how they are configured, how they are related to one another, and how the configurations and their relationships have changed over time.

## AWS Cost Explorer

AWS Cost Explorer is a tool that enables you to view and analyze your costs and usage. You can explore your usage and costs using the main graph, the Cost Explorer cost and usage reports, or the Cost Explorer RI reports. You can view data for up to the last 12 months, forecast how much you're likely to spend for the next 12 months, and get recommendations for what Reserved Instances to purchase. You can use Cost Explorer to identify areas that need further inquiry and see trends that you can use to understand your costs.

## AWS Shield Advanced

**CF, ELB, Route53, Global Accelarator**

AWS Shield can **handle the DDoS attacks. But it can not be attached directly to EC2 instances.** It requires to be attached to services such as CloudFront, Route 53, Global Accelerator, ELB or (in the most direct way using) Elastic IP (attached to the EC2 instance)

## AWS WAF(Web Application Firewall)

Layer 7  = HTTP

**CF, ALB, API Gateway, AppSync GraphQL API, Cognito User Pool**

AWS WAF is a web application firewall that helps protect web applications from attacks by allowing you to configure rules that allow, block, or monitor (count) web requests based on conditions that you define. These conditions include IP addresses, HTTP headers, HTTP body, URI strings, SQL injection and cross-site scripting.

By Defining **Web ACL(Web Access Control List)** Rules:

**Geographic (Geo) Match Conditions in AWS WAF**. This new condition type allows you to use AWS WAF to restrict application access based on the geographic location of your viewers. With geo match conditions you can choose the countries from which AWS WAF should allow access.

DDoS protection

SQL injection and Cross-Site Scripting (XSS)

Size constraints

**WAF has bot identification and remedial tools**

## AWS Firewall Manager

AWS Firewall Manager simplifies your administration and maintenance tasks **across multiple accounts** and resources for a variety of protections.

If you want to use AWS WAF across accounts, accelerate WAF configuration, automate the protection of new resources, use Firewall Manager with AWS WAF

AWS Firewall Manager security policies are **region specific**. Each Firewall Manager policy can only include resources available in that specified AWS Region.

## Amazon GuardDuty

can collect information from **VPC Flow Logs, CloudTrail Logs, DNS Logs and EKS Audit Logs**

- Intelligent Threat Discovery to protect your AWS Account
- cant setup EventBridge rules to be notified in case of findings (tragets AWS lambda or SNS )
- can protect against CryptoCurrency Attacks 

## Amazon Inspector

Automated Scurity Assessments

only for **EC2, Container Images ( ECR ), Lambda Functions**

report with AWS Security Hub 

send findings to Amazon EventBridge

## Amazon Macie

detect sensitive data. such as personally identifiable information (PII) -> notify using EventBridge



## Amazon FSx

- HPC + Linux -> FSx for Lustre

  FSx for Lustre makes it easy and cost-effective to launch and run the popular, high-performance Lustre file system. You use Lustre for workloads where speed matters, such as machine learning, high performance computing (HPC), video processing, and financial modeling. Amazon Fsx for Lustre is integrated with Amazon S3.

- windows -> FSx


## Service Catalog

Service Catalog allows organizations to centrally manage commonly deployed IT services, and helps organizations achieve consistent governance and meet compliance requirements. End users can quickly deploy only the approved IT services they need, following the constraints set by your organization.

- Self-service discovery and launch

