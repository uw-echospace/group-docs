# Cloud computing

Some topics to consider:
- What is the cloud?
- What cloud resources we use in the group?
- How is computing on the cloud different from computing on a local machine?
- How do I set up my credential to use on the cloud
    - best practices recommendations
- ...

  
At Echospace we use Amazon Web Services for some projects. Some common use cases have been:

* store some datasets and make them accessible to many people
* use powerful virtual machines or clusters when individual researchers' laptops are not enough
* set up dashboards that can be continuously run and available for demo
  


## Set up credentials 


* Different types of credentials 
    - [ec2 key pairs](
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html): you need those to connect to an ec2 instance
    - access keys (often stored in a `credentials.csv` or an `accessKeys.csv` file): those are used either through the aws client or other tools to programmatically use aws services
    - console log-in (stored in a `credentials.csv` file): you can use it to start/stop some services and monitor your resources 
    - [configuration and credential Files](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html) (for example, used to connect to data on private S3 buckets)
   
* how to store and use your credentials (ask Don for more details)
    - Advice from AWS: [multi-factor authentification](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable.html)
 
## Getting Started Tutorials: Overview

* [eScience Cloud 101](https://cloudmaven.github.io/documentation/aws_overview.html) tutorial 
* [AWS Skill Center](https://aws.amazon.com/training/skills-centers/seattle-skills-center/) 
* Dingrui: tutorials
* Billing (Valentina)
    - [Billing Page](https://us-east-1.console.aws.amazon.com/billing/home?region=us-west-2#/bills)
    - [Pricing of EC2 instances](https://aws.amazon.com/ec2/pricing/on-demand/)
    - [Pricing of S3 storage](https://aws.amazon.com/s3/pricing/) Note: while moving data into S3 is free, moving data out of S3 is expensive (it is called egress fee). Discuss with us if you plan to download large (greater than 100GB) datasets out of S3
    - [Pricing calculator](https://calculator.aws/#/)
          
* Jupyter Notebook and Python Scripts on EC2 (Caesar)
    - Instructions 
    - Starting with small instances for setup, and then increase type
Not too small, coz then mamba does not run 
    - Use Amazon Machine Image (AMI) Amazon Linux 2023 AMI
    - VSCode connect to EC2 (use Jupyter Notebook)
        - Install VSCode
        - Install remote SSH on VSCode
        - Add Pictures for this
        - Finish the rest of this
         
## Tagging Resources (Valentina)

Resources do not get tagged automatically by the user on AWS when services get started from the console. One needs to add them manually during set up or after the service gets started.

* Email
* Owner
* Project 
* Task 

## Moving resources between different providers/local-to-cloud (Valentina)
* [Rclone](https://rclone.org/)

## Extra tutorials
* cloud agnostic: [terraform](https://www.terraform.io/)
* prefect : [Prefect AWS](https://prefecthq.github.io/prefect-aws/)

## What people have used in the group?
* Hake ML Project (Caesar)
* EC2 Instances
    - Converting, Calibrating, Regridding, Mask Creation
    - Storing data for quicker use on EFS
    - Storing data for backup use on S3

## Advice to admins:
* Rotate keys (have a schedule)
* Check tags
* Check EC2 Volumes
* Check EFS and S3 Volumes
* Global View of ec2 instances (we can look in all regions)
* [CloudTrail](https://us-west-2.console.aws.amazon.com/cloudtrail/home?region=us-west-2#/events?ReadOnly=false)
    - Check what role is needed for users to see cloud trail
    - Check all zones


## Extra
* When to use cloud? Decision Tree Diagram (Valentina)
 
