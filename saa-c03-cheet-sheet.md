## Amazon S3

- S3 Transfer Acceleration

- S3 File Gateway

  ache recent access file

- S3 Lifecycle Policy

- S3 Object Lock enabled

- s3:PutObjectLegalHold

  The Object Lock legal hold operation enables you to place a legal hold on an object version. Like setting a retention period, **a legal hold prevents an object version from being overwritten or deleted.** However, a legal hold doesn't have an associated retention period and remains in effect until removed.

- preassigned URL

  preassigned URL is for upload or download for temporary time and for specific users outside the company. signed URL is for temporary access

## Amazon API Gateway



## NAT Gateway

NAT Gateway will be created Public Subnet and Provide access to Private Subnet

## Amazon ECS

- AWS Fargate

  AWS Fargate is a technology that you can use with Amazon ECS to run containers without having to manage servers or clusters of Amazon EC2 instances. With Fargate, you no longer have to provision, configure, or scale clusters of virtual machines to run containers. This removes the need to choose server types, decide when to scale your clusters, or optimize cluster packing. 

## Amazon DataSync

To automate the process of transferring the data from the on-premises SFTP server to an EC2 instance with an EFS file system, you can use AWS DataSync. AWS DataSync is a fully managed data transfer service that simplifies, automates, and accelerates transferring data between on-premises storage systems and Amazon S3, Amazon EFS, or Amazon FSx for Windows File Server. To use AWS DataSync for this task, you should **first install an AWS DataSync agent in the on-premises data center**. This agent is a lightweight software application that you install on your on-premises data source. T**he agent communicates with the AWS DataSync service to transfer data between the data source and target locations.**

## Gateway Load balancer

Gateway Load Balancers enable you to deploy, scale, and **manage virtual appliances**, such as firewalls, **intrusion detection** and prevention systems, and **deep packet inspection** systems. It combines a transparent network gateway (that is, a single entry and exit point for all traffic) and distributes traffic while scaling your virtual appliances with the demand.

A Gateway Load Balancer **operates at the third layer of the Open Systems Interconnection (OSI) model,** the network layer. It listens for **all IP packets** across all ports and forwards traffic to the target group that's specified in the listener rule. It maintains stickiness of flows to a specific target appliance using 5-tuple (for TCP/UDP flows) or 3-tuple (for non-TCP/UDP flows). The Gateway Load Balancer and its registered virtual appliance instances exchange application traffic using the [GENEVE](https://datatracker.ietf.org/doc/html/rfc8926) protocol on port 6081

## Amazon CloudFront distribution



## AWS Global Accelerator

HTTP + TCP 

## Amazon MQ



## Amazon SQS

- Standard queue
- FIFO queue

## Amazon Kinesis

## Amazon Athena

Athena helps you analyze unstructured, semi-structured, and structured data stored in Amazon S3. Examples include CSV, JSON, or columnar data formats such as Apache Parquet and Apache ORC. You can use Athena to run ad-hoc queries using ANSI SQL, without the need to aggregate or load the data into Athena.

## Amazon RedShift

## Amazon Glue

- AWS Glue tracks data that has already been processed during a previous run of an ETL job by persisting state information from the job run. This persisted state information is called a job bookmark. **Job bookmarks help AWS Glue maintain state information and prevent the reprocessing of old data.**

## AWS Snowball Edge 

​	On a Snowball Edge device you can copy files with a speed of up to 100Gbps. 70TB will take around 5600 seconds, so very quickly, less than 2 hours. The downside is that it'll take between 4-6 working days to receive the device and then another 2-3 working days to send it back and for AWS to move the data onto S3 once it reaches them. Total time: 6-9 working days. Bandwidth used: 0.

## Amazon Aurora

Aurora is a fully managed, MySQL-compatible relational database that is designed for high performance and high availability. Aurora Multi-AZ deployments **automatically maintain a synchronous standby replica in a different Availability Zone to provide high availability**. Additionally, Aurora Auto Scaling allows you to automatically scale the number of Aurora Replicas in response to read workloads, allowing you to meet the demand of unpredictable read workloads while maintaining high availability. This would provide an automated solution for scaling the database to meet the demand of the application while maintaining high availability.

## Amazon QuickSight

QuickSight **don't support IAM. We use users and groups** to view the QuickSight dashboard

## Amazon Elastic Block Store (Amazon EBS)

- Snapshot

  **A snapshot is constrained to the AWS Region where it was created.** After you create a snapshot of an EBS volume, you can use it to create new volumes in the same Region. For more information, see [Create a volume from a snapshot](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-creating-volume.html#ebs-create-volume-from-snapshot). You can also **copy snapshots across Regions**, making it possible to use multiple Regions for geographical expansion , data center migration, and disaster recovery. You can copy any accessible snapshot that has a `completed` status. For more information, see [Copy an Amazon EBS snapshot](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-copy-snapshot.html).

- Fast Snapshot Restore(FSR)

  Amazon EBS fast snapshot restore (FSR) enables you to create a volume from a snapshot that is fully initialized at creation. This eliminates the latency of I/O operations on a block when it is accessed for the first time. Volumes that are created using fast snapshot restore instantly deliver all of their provisioned performance.

## Amazon RDS

 Amazon RDS event notification doesn't support any notification when data inside DB is updated. You can use a SQS to do notification.

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

## AWS Network Firewall

AWS Network Firewall is a managed firewall service that provides filtering for **both inbound and outbound network traffic**. It allows you to create rules for traffic **inspection and filtering**, which can help **protect your production VPC**.

## Security / Access / Restriction

- IAM role

  Always remember that **you should associate IAM roles to EC2 instances**

## AWS Secrets Manager

AWS Secrets Manager is a secrets management service that helps you protect access to your applications, services, and IT resources. This service enables you to rotate, manage, and retrieve database credentials, API keys, and other secrets throughout their lifecycle.

- You can rotate secrets on a schedule or on demand by using the Secrets Manager console, AWS SDK, or AWS CLI.
- With Secrets Manager, you can store, retrieve, manage, and rotate your secrets, including database credentials, API keys, and other secrets. When you create a secret using Secrets Manager, it’s created and managed in a Region of your choosing. Although scoping secrets to a Region is a security best practice, there are scenarios such as disaster recovery and **cross-Regional redundancy that require replication of secrets across Regions**. Secrets Manager now makes it possible for you to easily replicate your secrets to one or more Regions to support these scenarios

## AWS Systems Manager Parameter Store

no auto rotation for keys

## AWS Key Management Service (AWS KMS)

- Server-side encryption with AWS KMS keys (SSE-KMS)

  SSE-KMS allows you to use keys that are managed by the AWS Key Management Service (KMS) to encrypt your data at rest. KMS is a fully managed service that makes it easy to create and control the encryption keys used to encrypt your data. With automatic key rotation enabled, KMS will automatically create a new key for you on a regular basis, typically every year, and use it to encrypt your data. This simplifies the key rotation process and reduces the operational burden on your team.

  

- aws:PrincipalOrgID

  the condition key aws:PrincipalOrgID can prevent the members who don't belong to your organization to access the resource

## AWS Config

Configuration changes= AWS Config

AWS Config provides a detailed view of the resources associated with your AWS account, including how they are configured, how they are related to one another, and how the configurations and their relationships have changed over time.

## AWS Cost Explorer

AWS Cost Explorer is a tool that enables you to view and analyze your costs and usage. You can explore your usage and costs using the main graph, the Cost Explorer cost and usage reports, or the Cost Explorer RI reports. You can view data for up to the last 12 months, forecast how much you're likely to spend for the next 12 months, and get recommendations for what Reserved Instances to purchase. You can use Cost Explorer to identify areas that need further inquiry and see trends that you can use to understand your costs.

## AWS Shield Advanced

AWS Shield can **handle the DDoS attacks. But it can not be attached directly to EC2 instances.** t requires to be attached to services such as CloudFront, Route 53, Global Accelerator, ELB or (in the most direct way using) Elastic IP (attached to the EC2 instance)



