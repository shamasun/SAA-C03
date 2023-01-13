## AWS Fundamentals
### 4.1 AWS Public vs Private Services
AWS Services come in two main types - Public and Private services
Terms Public and Private here refer to networking ONLY
Public services = accessible using Public end-points (like S3)
Private services = runs within a VPC. Things within VPC or connected to VPC can access.
For both there are permissions + networking
So, even though S3 is Public service, by defaul an identiy other than root user has no auth to access it.
Access detrmined by Networking + Permissions. Fo this lesson, we are concerned with the former.
There are three network zones
Public Internet zone: 
AWS Public zone: 
    - Not part of Public internet. 
    - Its a network connected to the Public internet. 
    - AWS public services (i.e., services with Public end-points) operate here (such as S3).
    - Accessed using internet as transit
AWS Private zone:
    - On-premise resources can connect via VPN or Direct Connect
    - EC2 instances are AWS private resources
    - VPCs run from here
        - Internet Gateway can be attached to it.
            - Allows access to AWS Public services, such as S3 in the AWS Public zone.
            - Allows access to EC2 (say) from Public Internet
                - Provided EC2 has allocated public IP address.
                - Architecturally, this is projecting EC2 into the AWS Public zone.

### 4.2 AWS Global Infrastructure
AWS Regions
    - Creation of AWS
    - Full deployment of AWS services
    - When interacting with a service, you are interacting with that service in a specific region
        - IAM, Route 53 are examples of Global services however
    -  Benefits of Regions
        - Geographic separation means isolated fault domain
        - Geopolitical separation. If you have data in the EU region, there is certainty that it wont end-up in China for example.
        - Loction control. Allows tuning your deployment for performance.
    - have a code (used in clid, code) an name (often iused in colnsole)
    - Availability Zone 
        - Failure is sometimes localized
        - isolated infra within a region. AZs are connected by high-speed networks.
        - allows, as a solution architect, to design solutions which distribute components across multiple AZs
        - can represent one or more data centers
        - no visibility from AWS on what an AZ is.
        - VPCs can be crated across AZs.
    - Resilience in AWS services
        - Globally resilient - IAM, Route 53
        - Region resilient - operats separate in each region
        - AZ resilient - 

AWS Edge Locations
    - Can't have AWS regions in all places as your customers
    - Hence Edge locations = Content Deliovery Networks. Sometimes edge computing
    - Useful for Netflix to cache TV shows in remorte locations
    - Helps with low latency

regions ajd edge locations commony use together by 


### 4.3 AWS Default Virtual Private Cloud (VPC)
Virtual network inside AWS
Is with 1 AWS account and 1 Region.
Regionally resilient service
Isolated from - 
    - Other VPCs
    - Public Internet
    - AWS Public zone
Two types of VPC in a region
    - Custom VPC (many can be had in a region)
        - used in most serious AWS deploiyments
        - because configurable basis ones need
        - Private and isolated by default.
        - have multiple CIDR ranges
    - Default VPC (= max of one per region)
        - lot less flexible than custom VPCs        
        - allocated a range of IPs = VPC CIDR
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
            - some services assume default VPC preswent. So, let it remain. Dont use if you dont want.
            - CIDR range is limiting for production deploymen
            - A /16 CIDR means, a large number of IP addresses. Higher the number, smaller the network.
            - A smaller /20 subnet is created in each AZ
            - Two /17 fit into one /16. Sixteen /20 subnets can fit into /16. That is, it can support 16 AZs
            - Default IGW, Security Group, and NACL are also created.
            - Anything placed in default VPC subnets gets a public IPv4 address. So services in here, will be in the Public zone. Specific to default VPC only.


Service o create private networks inside AWS
VPCs are useful in creating a
    - hybrid environment between AWS Private networks and On-premises networks
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