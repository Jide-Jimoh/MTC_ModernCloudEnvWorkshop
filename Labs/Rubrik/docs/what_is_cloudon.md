# What is CloudOn?

Rubrik's CloudOn feature allows the conversion of VMware vSphere, or Microsoft Hyper-V images, captured via backup on-premises, to be converted to a Microsoft Azure (VHD format), or Amazon Web Services (AMI format), native cloud image format, and launched in the respective cloud provider.

## What do customers use CloudOn for?

Rubrik's customers use CloudOn to provide a number of benefits in their business:

* **Test/Dev** - customers can create exact copies of their production servers in the cloud, in a sandboxed network. This ensure that application developers can build and test their applications in an environment which is representative of production, highly automatable, and runs the best cost model for this kind of workload
* **Disaster Recovery** - CloudOn allows customers to have their workloads pre-converted and ready to go in case of an on-premises data center. This has seen customers ditching their DR data centers and using the public cloud for their application DR
* **Application Mobility** - allows the customer to lift-and-shift their application to the cloud provider which most makes sense to them. This helps to ensure cost optimisation, allows workloads to exploit cloud-specific services which can be of benefit, and helps to avoid cloud lock-in

## How does CloudOn work?

There are two available methods to instantiate workloads in the public cloud; continually converting from a backup, or an on-demand conversion. These are discussed in more detail below:

### CloudConversion

CloudConversion is Rubrik's name for creating a new converted image each time a backup is taken on-premises. High level, this follows these steps:

1. Snapshot is taken on-premises, and stored on the Rubrik file system
1. Incremental changes are uploaded to the public cloud; these sit in the customer's S3 bucket or Blob Storage account
1. Once changes are uoloaded, a small single instance of the Rubrik software is launched in the cloud, this is controlled by the on-premises cluster
1. The backup data in the S3 bucket or Blob Storage account, which represents the latest snapshot, is ingested into this Rubrik cloud instance, and the image is converted to the cloud-native format
1. In the case of the Azure cloud, the image is written to a Blob Storage account in VHD format. In the case of AWS, this is written as an AMI to the customer's account

At this point the image is created and ready-to-go, meaning that it can be launched in under 10 minutes when needed. This takes place as a background process following the successful backup of an on-premises VM.

### On-Demand Conversion

Where customers wish to instantiate an older snapshot, or do not require this continual conversion, an on-demand conversion is used to convert and bring the VM image up in the public cloud in a single workflow. The process is described below:

1. Customer selects a VM snapshot from the Rubrik cluster, and clicks 'Launch on Cloud', the required VM size, security group, and network are selected through the Rubrik console
1. A small single instance of the Rubrik software is launched in the cloud, this is controlled by the on-premises cluster
1. The backup data in the S3 bucket or Blob Storage account, which represents the selected snapshot, is ingested into this Rubrik cloud instance, and the image is converted to the cloud-native format
1. In the case of the Azure cloud, the image is written to a Blob Storage account in VHD format. In the case of AWS, this is written as an AMI to the customer's account
1. The image file is launched via the cloud provider's APIs