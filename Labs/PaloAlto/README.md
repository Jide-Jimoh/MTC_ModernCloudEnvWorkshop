<img src="../../Images/paloalto.png" width="250">

# Palo Alto  Hands-On Lab

This lab guide aims to provide users with a hands-on experience in deploying the Palo Alto Network Firewall on the Azure environment. At the end of this lab, the users should have experience in creating and configuring Azure Resource Group which comprises of Azure Virtual Network (VNET), Availability Set (AvSet), Azure Load Balancer (ALB), User Defined Routes (UDR) and the Palo Alto Networks Firewall. 

The following is the network diagram of this lab. We will attempt to build this in the Azure environment. There will be 1 Virtual Network (vnet). Within the vnet, we will deploy 2 x Azure Load Balancers and 2 x Linux web servers behind the Palo Alto Networks Firewall. The inbound traffic from the internet will be load balanced by an external Azure Load Balancer (ALB). 

![Lab Diagram](./Images/paloalto-lab-arch.png)

# Lab Instructions
Please follow the lab instruction here: [APAC Azure Deployment Lab Guide](palab.docx)

<a name="CleaningUp"></a>

# Cleaning Up

Once you are done with the lab, unless you want to continue with these resources in Azure you can delete them.

1. In the browser, go to the **<a target="_blank" href="https://portal.azure.com/">Azure Portal</a>** (<a target="_blank" href="https://portal.azure.com/">https://portal.azure.com</a>), and click on the "**Resource Groups**", select the "***&lt;name&gt;group***" and on the "**Overview**" page, review its contents.  When you are ready, click the "**Delete**" button along the top.

1. On the "**Are you sure...**" page, enter your resource group name into the "**TYPE THE RESOURCE GROUP NAME**" box, and click the "**Delete** button along the bottom. Depending on how many resources are in the group, it may take a while for the deletion to complete.

    ***BE AWARE! WHEN YOU DELETE THE RESOURCE GROUP ALL OF THE RESOURCES IN IT WILL BE DELETED AS WELL.  MAKE SURE YOU ARE DELETING THE CORRRECT RESOURCE GROUP AND THAT YOU INTEND TO DELETE ALL THE RESOURCES IN THE GROUP BEFORE PROCEEDING.***

1. It's possible that some tiles will be left on your dashboard event after deleting the resources they represent.  You can remove them yourself just by hovering over them with your mouse, clicking on the ellipsis ("**...**") and choosing "**Unpin from dashboard**".

1. After deleting the resource group and all the resources that were provisioned in this lab, you won't have recurring charges or resource utilitization related to the work you did here.