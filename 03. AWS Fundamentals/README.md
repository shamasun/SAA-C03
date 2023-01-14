## AWS Fundamentals
### 4.1 AWS Public vs Private Services
- "Public" and "Private" used in networking context
- Public services = accessible using Public end-points (like S3)
- Private services = runs within a VPC. Things within VPC or connected to VPC can access.
- Access = function of Networking + Permissions.
    - So, even though S3 is Public service, by default an identity other than root user has no authorization to access it.
    - In this lesson, concerned with networking.
- There are three network zones
    1. Public Internet zone
    2. AWS Public zone
        - Not part of Public internet. 
        - Network connected to the Public internet. 
        - AWS public services (i.e., services with Public end-points) operate here (such as S3).
        - Accessed using internet
    3. AWS Private zone
        - VPCs run from here
            - Internet Gateway (IGW) can be attached
                - Allows access to AWS Public services, such as S3.
                - Allows access to Public Internet 
                    - Provided EC2 (say) has allocated public IP address.
                    - Architecturally, this is projecting EC2 into the AWS Public zone.
        - On-premise resources can connect via VPN or Direct Connect
        - EC2 is an example of a AWS private resource

### 4.2 AWS Global Infrastructure
AWS Regions
- AWS' notion of a region
- When interacting with a service, you are interacting with the service in a specific region
    - IAM, Route 53 are examples of Global services however
-  Benefits of Regions
    - Geographic separation $\implies{}$ isolated fault domain
    - Geopolitical separation. Data in the EU region? Certainty that it wont end-up in China.
    - Location control. Allows tuning your deployment for performance.
- Code used in CLI and name often used in console
- Availability Zone 
    - Isolated infra within a region $\implies{}$ Failure is localized
    - AZs are connected by high-speed networks.
    - can represent one or more data centers. No visibility from AWS.
    - VPCs can be crated across AZs.
- Resilience in AWS services
    1. Global resilience - IAM, Route 53
    2. Region resilience - operates separate in each region
    3. AZ resilience

AWS Edge Locations
- Content Deliovery Networks. Sometimes edge computing.
- Can't have AWS regions in all places as your customers
- Useful for Netflix to cache TV shows in remote locations. Helps with low latency

### 4.3 AWS Default Virtual Private Cloud (VPC)
- Virtual network inside AWS
- Spans 1 AWS account and 1 Region.
- Regionally resilient
- Isolated
- Two types of VPC in a region
    - Custom VPC
        - many can be had in a region
        - because configurable, used in most serious AWS deployments
        - Private and isolated by default.
        - can have multiple CIDR ranges
    - Default VPC
        - max of one per region
        - lot less flexible than custom VPCs        
        - VPC CIDR is always = 172.31.0.0/16
        - AZs within a VPC (assuming you want resilience) 
            - have subnets (carved out sub-ranges of CIDR IPs). 
            - Come by default. Cannot be changed.
            - An example
                - SN-A(say) = 172.31.0.0/20 $\implies{}$  [172.31.0.0,  172.31.15.255] 
                - SN-B(say) = 172.31.16.0/20 $\implies{}$ [172.31.16.0, 172.31.30.255]
                - SN-C(say) = 172.31.32.0/20 $\implies{}$ [172.31.32.0, 172.31.47.255]
        - Facts
            - 1 per region.
            - Can be deleted and reinstated
            - some services assume default VPC present. So, let it be.
            - CIDR range may be limiting for production deployments.
            - A /16 CIDR means, a large number of IP addresses. Higher the number, smaller the network.
            - A smaller /20 subnet is created in each AZ
            - Two /17 fit into one /16. Sixteen /20 subnets can fit into /16. That is, it can support 16 AZs
            - Default IGW, Security Group, and NACL present.
            - Anything placed in default VPC subnets gets a public IPv4 address. So services in here, will be in the Public zone. Specific to default VPC only.

- VPCs are useful in creating
    - hybrid environment of AWS Private networks and On-premises networks
    - multi-cloud deployment

### 4.4 Elastic Compute Cloud (EC2) Basics
### 4.5 My First EC2 Instance - PART1
### 4.6 My First EC2 Instance - PART2
### 4.7 Simple Storage Service (S3) Basics
### 4.8 My First S3 Bucket
### 4.9 CloudFormation (CFN) Basics
Template to create AWS Infrastructuere
Also update template and reapply
Even to delete infra 
YAML or JSON
All templates have a resources section. This is what tells CF waht to do
    - Only Mandatory part of a CF template
    - YAML
        - If you have a AWSTemplateFormatVersion section, the Description section must follow immediately.
        - Metadata section: control how the UI presents
        - Parameters section: Add fields to prompt user for more information. Can have settings on which are vlid entries.Say, AllowedValues key with values = [t2.micro, m1.small, m1.large]
        - Mappings section: allows creation of lookupm tables
        - Conditions section: Decision making in the template. Conditional creation of resources.
        - Outputs: 

### 4.10 Simple Automation With CFN
### 4.11 CloudWatch (CW) Basics
### 4.12 Simple Monitoring with Cloudwatch
### 4.13 Shared Responsibility Model
### 4.14 High-Availability vs Fault-Tolerance vs Disaster Recovery
### 4.15 Route53 (R53) Fundamentals
### 4.16 Registering a Domain
### 4.17 DNS Record Types