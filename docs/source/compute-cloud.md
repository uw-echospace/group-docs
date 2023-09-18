# Cloud computing
  
At Echospace we use Amazon Web Services for some projects. Some common use cases have been:

* store some datasets and make them accessible to many people
* use powerful virtual machines or clusters when individual researchers' laptops are not enough
* set up dashboards that can be continuously run and available for demo
  


## Set up credentials 


* Different types of credentials 
    - [ec2 key pairs](
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html): you need those to connect to an ec2 instance
    - [access keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html) (often stored in a `credentials.csv` or an `accessKeys.csv` file): those are used either through the [AWS Command Line Interface](https://aws.amazon.com/cli/) or other tools to programmatically use aws services
    - [console log-in](https://docs.aws.amazon.com/signin/latest/userguide/introduction-to-iam-user-sign-in-tutorial.html) (stored in a `credentials.csv` file): you can use it to start/stop some services and monitor your resources 
    - [configuration and credential files](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html): those files have specific structure and are useful when storing different configurations
   
* Security of credentials
    - It is crucial to be very cautious when managing security credentials. A danger to commit credentials to github and make them public. There are credential hackers who regularly scan github for credentials and use them as soon as they become exposed. To avoid this problem. NEVER PUT CREDENTIALS DIRECTLY IN CODE (SCRIPTS OR NOTEBOOKS). Do not do this even temporarily, as you might forget. It is best to store them in files and read the files from the code. Include the credential filename in your `.gitignore`.
    - Advice from AWS: [multi-factor authentification](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable.html)
 
## Getting Started Tutorials: Overview

* [ec2 instance set-up](https://frosted-hamster-458.notion.site/Set-up-env-ec2-faeceebfc16f45509d3f4c18c25f2c22) by @ldr426
* [eScience Cloud 101](https://cloudmaven.github.io/documentation/aws_overview.html) tutorial 
* [AWS Skill Center](https://aws.amazon.com/training/skills-centers/seattle-skills-center/)

* Billing
  It is important to learn to monitor AWS billing even as a new user/.
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
         
## Tagging Resources

Resources do not get tagged automatically by the user on AWS when services get started from the console. One needs to add them manually during set up or after the service gets started. Please, the following tags for your resources.

* Email
* Owner
* Project 
* Task 

## Moving resources between different providers/local-to-cloud
* [Rclone](https://rclone.org/)

## Cloud Agnostic Tools   

* [terraform](https://www.terraform.io/): terraform allow scripting the cloud set up commands and works with different cloud providers
* [fsspec](https://filesystem-spec.readthedocs.io/en/latest/): Filesystem Spec is a Python tool to access local, remote and embedded file systems and bytes storage in a unified way 
* [Prefect AWS](https://prefecthq.github.io/prefect-aws/): Prefect is a general data workflow tool which allows integration with AWS, but can be set up with other providers.

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
 
