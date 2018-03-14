# Deploying Nasuni Filer on Azure

> **Difficulty**: Intermediate (assumes basic familiarity with Azure and Networking)

> **Time**: Approximately 75+ minutes

Nasuni delivers an advanced storage solution using a cloud infrastructure. The core technology is a
next-generation storage controller – the Nasuni Filer – that offers the security and performance of
traditional storage, while adding unlimited scalability, automatic offsite protection, and global multi-site
access to files. The Nasuni system is managed through a single, small-footprint point of control within
the enterprise’s data center.
The Nasuni Filer is an on-premises storage device supporting NFS, CIFS, FTP/SFTP, iSCSI, and HTTP/
REST protocols. The Nasuni Filer is fully integrated with Active Directory, LDAP, Distributed File System
(DFS), and Windows Previous Versions. It includes a high-performance cache and takes periodic
snapshots that enable file-level restores. Its reach and capacity far exceed those of a traditional
controller, however, because it does not rely only on memory and local disk to manage its data: it has
the entire capacity of the cloud at its disposal. All data is deduplicated, compressed, and encrypted
before storage.

This lab outlines the steps necessary to get your Nasuni Filer up and running on the Azure platform.

# Lab Instructions

Please follow the lab instruction here: [Nasuni Filer Quick Start Guide](QuickStartGuide.pdf)

# Cleaning Up

Once you are done with the lab, unless you want to continue with these resources in Azure you can delete them.

1. In the browser, go to the **<a target="_blank" href="https://portal.azure.com/">Azure Portal</a>** (<a target="_blank" href="https://portal.azure.com/">https://portal.azure.com</a>), and click on the "**Resource Groups**", select the "***&lt;name&gt;group***" and on the "**Overview**" page, review its contents.  When you are ready, click the "**Delete**" button along the top.

1. On the "**Are you sure...**" page, enter your resource group name into the "**TYPE THE RESOURCE GROUP NAME**" box, and click the "**Delete** button along the bottom. Depending on how many resources are in the group, it may take a while for the deletion to complete.

    ***BE AWARE! WHEN YOU DELETE THE RESOURCE GROUP ALL OF THE RESOURCES IN IT WILL BE DELETED AS WELL.  MAKE SURE YOU ARE DELETING THE CORRRECT RESOURCE GROUP AND THAT YOU INTEND TO DELETE ALL THE RESOURCES IN THE GROUP BEFORE PROCEEDING.***

1. It's possible that some tiles will be left on your dashboard event after deleting the resources they represent.  You can remove them yourself just by hovering over them with your mouse, clicking on the ellipsis ("**...**") and choosing "**Unpin from dashboard**".

1. After deleting the resource group and all the resources that were provisioned in this lab, you won't have recurring charges or resource utilitization related to the work you did here.
