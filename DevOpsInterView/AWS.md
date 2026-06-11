# AWS interview Question

- **Explain the difference between Regions and Availability Zones.**
  - _Regions_: Regions is an independent geographic area where a cloud provider operator.
  - _Availability Zones_: Is is an isolated, distinct data center facility within that region.

- **What is the significance of the ”Edge Location”?**
  - A edge location is a physical data center strategically placed around the world to bring cloud computing, caching and network traffic processing physically closer to end users.

- **How do you design a highly available architecture on AWS?**
  - Must Eliminate all single points of failures by distributing components across multiple physical locations. decoupling infrastructures layers. and automating

- **What is a VPC (Virtual Private Cloud)?**
  - Vpc are the logical isolating provider, private networking environment withing a private cloud. It allows us to run cloud resources, and database isolation.

- **Difference between Public Subnet and Private Subnet.**
  - A public subnet is allow to access internet directly. and hosts external facing resources (like web server).
  - A private subnet has no direct route to the internet and hosts sensitive backend resources (like database and api resources) that must shielded from external access.

- **What is an Internet Gateway (IGW)?**
  - An Internet Gateway is a horizontal scaled, highly available networking components that serves as a bridge between a private isolating network and the public network.

- **Explain the role of a NAT Gateway.**
  - A NAT Gateway is a Network Address Translation (NAT) service. You can use a nat gateway so that the instance in public subnet can connect to service outside your vpc. But external services can't initiate a connection with those instances.

- **Difference between Security Groups and NACLs(Network Access Control Lists).**
  - _Security Group_ : Security Group implement on instances level. Support allows rules only.
  - _NACLs_ : Operate on subnets level. Support allows and deny rules

- **What is VPC Peering? What are its limitations?**
  - VPC peering allows a direct connection between 2 different VPC. Without using public Ip. Then can communicate with the private Ip.

- **Explain AWS Transit Gateway.**
  - AWS Transit Gateway is a managed, highly available cloud router that acts as a central hud to connect your VPC, On premiss datacenter, and network branch files

- **How do you connect an On-Premise data center to AWS? (Direct Connect vs VPN).**
  - Connecting an on-premises data center to AWS is typically achieved using either AWS Site-To-Site VPN or AWS Direct Connect. AWS VPN creates secures IPsec(Internet Protocol Security) that provides a encrypts tunnel that secure communications between devices.

- **What is Route 53? Explain its routing policies (Weighted, Failover, Latency).**
  - Route 53 is a highly available and scalable Domain Name System (DNS) web service by AWS.
  - _Weighted_ : Allows you to assign proportional weight or percentages to multiple resources for tha same domain name . Like 20% weight distributed of server A. and 80% Weight distributed to server B.
  - _Failover_ : Failover routing is used for disaster recovery by creating a Active/Passive setup
  - _Latency_ : Latency routing is design to improve the performance of your application for global users by connecting them to the AWS region that provides faster response time.

- **What is the purpose of an Elastic IP?**
  - Elastic Ip served a stable Ip ec2. Even if the server get restart or stop the Elastic Ip remain Same.

- **How do you secure data in transit within a VPC?**
  - Secure Data Transit within Virtual Private Cloud (VPC) requires encrypting traffic between resources and Isolation network path using VPC encryption Control.

- **What is an Application Load Balancer (ALB) vs Network Load Balancer (NLB)?**
  - _ALB_ : Application load balancer route traffic based on application level content (like URLs and HTTP headers) Ideal for web content.
  - _NLB_ : Network Load balancer route traffic at the transport layer (TCP/UDP) based on Ip and port

# AWS Storage

- **What are the S3 storage classes? (Standard, IA, Glacier, Deep Archive).**
  - S3 (Simple Storage Services) offers storage services. And the type is based on the price and accessibility.
  - _Standard_: Frequently accessed, Active Data.
  - _IA_ : Data Access less then a month.
  - _Glacier_ : Long term archive data.
  - _Deep Archive_ : The lowest-cost storage is the cloud

- **Explain S3 Bucket Policies vs IAM Policies.**
  - _S3_ : Resources based Policy, S3 bucket Only, Only able to control s3 bucket and resources .
  - _IAM Policy_ : Identity based policy, IAM Users, Groups, or Roles. Can control Almost any AWS Services .

- **How does S3 Cross-Region Replication work.**
  - S3 Cross-Region automatically and asynchronously copy object and host to another zones. ByDefault s3 do that work

- **What is EBS (Elastic Block Store)?**
  - It is a high performance, block level storage service to design to be used with AZ virtual storage.

- **Difference between GP2, GP3, IO1, and IO2 volumes.**
  - _GP1, GP2_ : GP1 and GP2 are cost-effective general-purpose SSDs
  - _IO1, IO2_ : IO1 and IO2 are high-performance IOSP design for critical purpose.

- **EFS vs. EBS**
  - _EFS (Elastic File System)_ : It is a shared filed resources that can be accessible to multiple server or ec2 instance via NFSv4 protocol
  - _EBS (Elastic Block Storage)_ : It is a high performance blocked storage design to attack to a single ec2 instance like a physical storage device.

- **How do you backup an EBS volume? (Snapshots).**
  - It is a POT backup . where the EBS volume is snapshot has been taken. and attached to a s3 driver.

- **What is AWS Storage Gateway?**
  - It is a hybrid cloud storage that connect to on-premiss server to unlimited cloud storage.

- **Explain S3 Versioning and its benefits.**
  - It is a feature that retains multiple variants (version) of an object in a single s3 bucket . it's like a version control system.

- **What is a pre-signed URL in S3?**
  - It is a secure temporary url that are provide to access the object inside the s3 buckets
