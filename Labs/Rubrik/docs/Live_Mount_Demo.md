# Live Mount Demo
Here is a video that will show how to use Live Mount for SQL Server

[Rubrik 4.1 SQL Demo](https://youtu.be/OXosomJ1jRs?t=1439)

The steps to perform a SQL Live Mount are as follows:
1. In the search bar, find a database that you want to Live Mount.
1. Click the link on the left panel that for the **Latest Recovery Point**. You can also select any valid restore point from the panel on the right.
1. Click the **elipsis** on the right panel.
1. Click **Mount**.
1. Select the host where you would like the database to be mounted to.
1. Click **Next**.
1. Select the instance to mount the database to.
1. Enter a name for the Live Mount database. Keep in mind this name must be unique to the server as you cannot have more than one database with the same name on a given SQL Instance.
1. Click **Mount**.

Depending upon size of the database, the proces will finish within 1-3 minutes. 

You will be able to see and interact with the database via SSMS or other methods like Powershell, SSRS, SSAS, PowerBi, etc. 
