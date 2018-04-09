# Demonstrating Rubrik CloudOn

This guide provides instructions on how to demonstrate the use of Rubrik's CloudOn functionality. Details on what CloudOn is, and how it works, can be found in the [What is CloudOn?](what_is_cloudon.md) guide.

1. Logon to the Rubrik cluster at **`TBC`** using the following credentials:

    Username | Password
    --- | ---
    mtcbosadmin | \<your password\>
1. Under the 'SLA Domains' widget, select 'MTC-BOS-CloudOn'
1. Here we can see the details of this SLA domain, the SLA domain is configured with the following settings:
    * Take a backup every day, and retain these for 7 days
    * There is no snapshot window configured, so backups can be taken at any time
    * There is no replication configured on this SLA domain
    * Snapshots are stored locally for 7 days, but are also instantly archived to an archival location (in this case an Azure Blob Storage account) where they are retained for 7 days
1. We can see the two Virtual Machines which belong to this SLA Domain:
    * **dnn-web01** - this is an IIS server, running Windows Server 2012R2, and hosting the [DNN](http://www.dnnsoftware.com/) .NET CMS software web component
    * **dnn-sql01** - this is a SQL Server database server, running Windows Server 2012R2, and hosting the SQL database component for the DNN application
1. In the bottom pane, click on one of the Virtual Machines
1. Select today's date from the calendar view, you will be able to see:
    * The time of the snapshot
    * Whether the snapshot is uploaded to the archive location (indicated by an icon to the right of the time of a Rubrik cluster and a cloud)
1. Click the ellipses button next to the most recent time (three dot characters), and you are presented with three options:
    * **Mount** - this is used to mount the Virtual Machine snapshot back into a vSphere environment, in this case the VM is presented with network devices disconnected
    * **Instantly Recover** - this is similar to 'Mount', but deprecates the existing VM by powering off and renaming it, replacing it immediately with the Virtual Machine snapshot
    * **Export** - this exports the Virtual Machine snapshot as a new VM to an existing datastore
    * **Browse Files** - this lets the user browse, and restore or download files from the Virtual Machine's filesystem
    * **Launch on Cloud** - this takes the Virtual Machine snapshot and starts it in the cloud (as described in the [What is CloudOn?](what_is_cloudon.md) guide)
1. Select 'Launch on Cloud', then select the 'Azure' bullet, you will be offered the following options:
    * **Location Name** - select 'Azure:rubrik-archive' here, you should see this say 'Image Exists', meaning that the conversion has already taken place, and the image is present in the Azure account
    * **Virtual Machine Size** - the Rubrik software will suggest the most appropriate VM size for the workload, but this can be customised through this dropdown
    * **VNet** - the VNET subnet to launch the VM in, select 'FrontEnd' here
    * **Network Security Group** - the NSG to apply to the VM, select 'T3_NSG_INT' here
1. Click 'Submit', the launch action can be monitored from the VM page in the Rubrik console

Now the machine has launched it should be visible in the Azure console, locate the VM in here and login via the [Rubrik jump box](./rubrik_jump_box.md) in the Azure account:

Credentials for the two instantiated virtual machines are:

Server | Username | Password
--- | --- | ---
dnn-web01 | Administrator | \<your password\>
dnn-sql01 | Administrator | \<your password\>