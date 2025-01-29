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

  **Here the sudo vs su debate, sudo is super user do and su is used to switch the user**
  **yum is the package manager which can be RedHat or anything (Yellowdog Updater, Modified), basically a package manager for the unix like service**
  **httpd is the Apache HTTP Server, which is a widely used web server software. Web server software means that we can install and work on softwares on the web on this server, its an online pc for web softwares**

  - systemctl, systemctl is a versatile and essential tool for managing services and system states in Linux distributions
  - sudo systemctl start <service_name>
  - sudo systemctl start httpd ( The command activates the Apache HTTP Server service, allowing it to begin handling incoming HTTP requests. )
  - 



