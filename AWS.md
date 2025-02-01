# Cloud Computing Services 

IaaS - Linux / Windows - EC2 
PaaS - Linux / Windows + Apache + MySQL + PHP - Elastic 
SaaS - Linux / Windows + Apache + MySQL + PHP + Software/ Apps - Chime

Before IaaS come on premise which means everything is managed by the organization. Local cloud for an organization

Cloud Computing Deployment Models :-
- Public (Cloud)
- Private (On-Premises) 
- Hybrid (Public Cloud + Private Cloud)


EC2 - Elastic Compute Cloud 
EC2 allows users to rent virtual machines with varying configurations of CPU, memory, storage, and networking capacity, enabling them to perform computations,
run applications, and handle data processing tasks without the need to invest in physical hardware.

Compute refers to the resources and processing power provided to the EC2 servers

## So how do you launch a VM on PC 

- You have a laptop (Hardware)
- OS installed
- VM software (VMware)
- VM1 instance

- Launcing an instance on EC2
- AWS hardware
- PV/HVM
- Instance 1 or 2

VPC - Virtual Private Cloud - Used to create a separate isolated network 

# Connecting to the EC2 instance

- We can connect using Putty or Mobaxtrem
- Launcing an Apache web server on EC2
- sudo yum install httpd

  **Here the sudo vs su debate, sudo is super user do and su is used to switch the user       ......
  yum is the package manager which can be RedHat or anything (Yellowdog Updater, Modified), basically a package manager for the unix like service             .......
 httpd is the Apache HTTP Server, which is a widely used web server software. Web server software means that we can install and work on softwares on the web on this server, its an online pc for web softwares**

  - systemctl, systemctl is a versatile and essential tool for managing services and system states in Linux distributions
  - sudo systemctl start <service_name>
  - sudo systemctl start httpd ( The command activates the Apache HTTP Server service, allowing it to begin handling incoming HTTP requests. )
  - systemctl enable httpd
  - Incoming HTTP requests mean that you can access via web page using the address
  - Windows client can use putty to connect and linux client can use ssh
  - sudo -s (to start a new shell session with root privileges)
  - dnf -y install httpd PHP (dnf is successor of yum -y is for yes, this is for installing php)
  - cat >index.html (index.html is the file using this we can edit the file and then using cat we can view the file)
 
- ssh -i /path/to/private_key.pem user@hostname (This is the path to the private key file you want to use for authentication. It is typically a file with a .pem or .key extension)


  ## Storage
  - Direct Attach Storage (DAS): like pendrive, USB, Hard Diskm instance storage(EBS) - for cloud
  - Network Attached Storage (NAS): Can be accessed by all the users in a local network, also called EFS(Elastic File System)-for cloud . One PC becomes the master or server and shares it to nearby PC's. another example is a printer
  - Storage Area Network (SAN): EBS(Elastic Block Store)-for cloud, data is stored in data blocks and not file system. Data blocks means C:, D: etc these storage blocks
  - Simple Storage Service (S3): to store the objects, data can be stored on a URL
 
- fdisk -l (list all the disks available)
- mount /dev/xvdf1  /ebs (ebs is being mounted in the linux instance)
- df -h (report file system disk space usage df -kh will give the result in kB)
- So basically the hard disk can be included in the cloud VM using the AWS account and SAN, then this hard disk is being mounted above
- umount /ebs

**AMI**

So now let's say we create a VM, AMI (Amazon Machine Image). This VM need storage/hard drive. 
- If we launch an EC2 instance for compute, we can either use EBS or Instance Store
- Instance Store is temporary, once we terminate the EC2, data is gone
- Let's say we create an EC2 in AZ1 aread using EBS, then we can take EBS snapshots
- These snapshots take full backup on the first time and then it is incremental, these backups are stored in S3
- Now using this S3 we can create a new VM in any other region
- WE can also transfer files between 2 instances using EFS


**Launching an Instance**

- Name
- AMI
- Instance Type
- Key pair
- Network Settings
- Configure storage


**S3**

- We can store objects in S3 using a link so we don't need to initiate an instance
- create a bucket in some region
- We can make the bucket and objects public as well
- For this we need to follow the bucket policy

- Bucket Versioning - to revert to the older version

- Launch static website using S3
- There should be an HTML file in the bucket, then there is an option to host the website, whatever the html file holds become the website's script
- Amazon Athena can be used to do simple query SQL on S3
- Amazon Redshift Spectrum does more complex SQL queries on large datasets

**RDS**
- Relational Database Service
- Six database engine available are Amazon Aurora, MariaDB, MySQL, PostgreSQL, Oracle and SQL Server
- AWS Database Migration Service (DMS) can be used to migrate existing databases to Amazon RDS.

**DynamoDB**
- Here we use partition key and storage key
- it is automated on the aws website, just like interana we used to use
- We can enter the attributes and the values of partition and storage key to retrieve the data

Multiple NoSQL databases are supported :-
Key Value - Pairs of key and it's value
Document - Amazon DocumentDB, stored like in JSON {}
Graph - Amazon Neptune
In Memory - Amazon DynamoDB
Amazon Elasticsearch Service


**VPC**
- Virtual Private Cloud
- It has different ranges of IP address some start from 192, some from 172, some from 10
- so within a VPC we have something called a subnet, which is basically a range of IP addresses
- within a subnet we can create an instance, so like VPC will be for a region and we create our private/public subnet which has only our instance
- Then we have public/private routing table and vpc will also have a main route table
- VPC can be created using AWS console and then subnets within it
- echo "Apache Web Server launched in Public Subnet">index.html (this texts get stored in the file and displays the output also)
- Route Table is the set of rules where the network traffic is directed.
- resources in the VPC(EC2) and the internet, this connection is established using the internet Internet gateway
- Just like a city can have different neighborhoods with different rules (e.g., traffic flow, security), a VPC can have subnets with different access control rules
  (public or private).
- Each neighborhood (subnet) can have its own road system (IP addressing), and the roads are controlled by traffic signs (network ACLs and route tables).

# Custom VPC setup 

- Setup VPC lab
- create custom vpc (ourvpc)
- create 2 public and 2 private subnets
- create internet gateway (ourig) and attach to VPC
- create and config routing table (public routing table)
- create webserver security group and add rules (webserver)
- Launch internet facing linux apache web server instance (webhosting)
- create database security group and add rules (database)
- private subnets for database (db-subnet)
- launch backend RDS instance (ourdb)
- connect to webserver instance using Putty
- deploy simple PhP/MySQL application in custom VPC 



