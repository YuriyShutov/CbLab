## Specify the Temporary Instance

On this wizard page, you can select whether you need to use a temporary instance when restoring an [image-based backup](/chapter1/step-3-choose-data-to-restore/34-restore-a-disk-image-or-network-share.md).

![](/assets/image-based-restore-to-ami-temp-instance.png)

These two options are described below.

* **Do not use temporary instance **  
  This option enables copying your files via a local computer, which is usually slower and depends on the local Internet connection speed.

* **Use temporary instance **  
  This option enables faster copying of your files at a higher cost, which depends on the instance type and running time of the restore process.

First, you need to select an existing, or specify a new _"S3"_ or _"S3 China"_ instance account. See the following article to learn how to add a new S3 account to CloudBerry Backup: [Signing up for Amazon S3](https://help.cloudberrylab.com/cloudberry-backup/signing-up-for-the-cloud/amazon-aws/signing-up-for-amazon-s3).

> Please make sure that the specified account has all required [EC2](/concepts/permissions.md) and [S3](https://docs.aws.amazon.com/AmazonS3/latest/dev/s3-access-control.html) permissions.

After selecting an account, specify the main settings of a target temporary instance:

* **Region**

  Amazon EC2 is hosted in multiple locations world-wide that are composed of separate geographic areas _\(regions\)_. Amazon EC2 provides you with the ability to place resources, such as instances, and data in multiple locations. Resources are not replicated across regions unless you do so specifically.

  > Please be informed that transferring data between different regions takes more time than performing data transfer within a single  region.  
  > When restoring a disk for an existing virtual machine, the disk must belong to the same Availability Zone as the  machine to which you are going to attach the disk.
  >
  > See [Regions and Availability Zones](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html) for more information.

* **Instance type**

  Amazon EC2 provides a wide selection of instance types optimized to fit different use cases, such as computing, memory use, accelerated computing and optimized storage.

  > We do not recommend that you use "**.micro**" or "**.nano**" configurations as a temporary instance \(such as **"t2.micro"** or **"t2.nano"**\), as well as extra large instances \(such as "**t2.xlarge**"\). Please consider using medium or large t- instances instead.  
  >   
  > Please be informed that not all instance types may be available in different regions. Occasionally, some instance types may become temporarily unavailable in certain Availability Zones due to service maintenance performed by AWS, in which case you need to switch to a different Availability Zone.  
  >   
  > See [Amazon EC2 Instance Types](https://aws.amazon.com/ec2/instance-types/) to learn about the available EC2 instance configurations.

* **Subnet**

  A virtual private cloud \(VPC\) is a virtual network dedicated to your AWS account. It is logically isolated from other virtual networks in the AWS Cloud. You can launch your AWS resources, such as Amazon EC2 instances, into your VPC.

  > A VPC spans all the Availability Zones in the region. After creating a VPC, you can add one or more subnets in each Availability Zone.
  >
  > See [VPCs and Subnets](https://www.gitbook.com/book/yuriyshutov/restore-wizard-draft/edit#) for more information[.](https://www.gitbook.com/book/yuriyshutov/restore-wizard-draft/edit#)

* **Security group**

  AWS enables you to increase security in your VPC by using [_security groups_](https://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_SecurityGroups.html) that act as a firewall for associated Amazon EC2 instances, controlling both inbound and outbound traffic at the instance level.

  > When using a temporary instance for restoring your disk image, please make sure that the security group of a subnet assigned to the temporary instance will not close the internet access.

  The wizard indicates whether your [VM import](https://docs.aws.amazon.com/vm-import/latest/userguide/what-is-vmimport.html) role is configured property for the selected account, because AWS will not perform input operations without appropriate permissions. You can create a VM import role in one of the following ways:

  * You can [manually configure a VM import role](https://www.cloudberrylab.com/blog/how-to-configure-vmimport-role/);

  * You can grant the required IAM permissions to an [IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups.html) whose account is used for restoring backups.

    The wizard will automatically create a VM import role when it detects that none of the above configurations are available.

* **AMI                                                    
  **Enables you to select a target [Amazon Machine Image](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html).

* **EBS volume type**

  Amazon EBS \(Elastic Block Store\) provides the following volume types, which differ in their performance characteristics and price, so that you can tailor your storage performance and costs to the requirements of your applications. CloudBerry Backup supports the following volume types:

  * **General Purpose SSD \(gp2\)                                            
    **A general purpose SSD volume that balances price and performance for a wide variety of workloads.

  * **Provisioned IOPS SSD \(io1\)                                            
    **The highest-performance SSD volume for mission-critical low-latency or high-throughput workloads.

  * **Magnetic \(standard, a previous-generation type\)                                            
    **A previous generation HDD. If you need higher performance or performance consistency than previous-generation volumes can provide, we recommend that you consider using _General Purpose SSD \(gp2\)_ or other current volume types.

  > See [Amazon EBS Volume Types](https://www.gitbook.com/book/yuriyshutov/restore-wizard-draft/edit#) to learn more.

Please be informed that CloudBerry Lab applications have no control over the processing time required to accomplish an image restoring process. Consider the following steps that are required to restore a disk image on a temporary instance:

1. Launching a temporary machine, which takes **4** minutes on average.
2. Installing a Remote Desktop Protocol \(RDP\) client. 
3. Processing an image-based backup. The time required to perform this task depends on the image that is being restored.
4. Processing the created image by AWS. Performing this task takes the longest time, which depends on the image size, location and other factors.

> AWS does not guarantee that a restoring process will be terminated when a restored machine fails to meet any requirements.
>
> If a restore process has failed for any reason, you can try to customize the source machine's settings according to [general AWS recommendations](https://docs.aws.amazon.com/vm-import/latest/userguide/vmimport-troubleshooting.html).



