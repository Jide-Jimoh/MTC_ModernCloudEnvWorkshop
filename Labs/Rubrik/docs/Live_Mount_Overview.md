# Live Mount Overview
SQL Server Live mount for Rubrik 4.0 is an exciting new technology that allows for a user to mount a SQL Server backup in Rubrik as a live database on any host and instance where the Rubrik connector is installed. The database files themselves are hosted directly on the Rubrik appliance via an SMB3 share, but in all other respects is a standard database. This allows for quick access to the database for a variety of use cases. The Live Mount is a read/write version of the database, allowing the user to manipulate the Live Mount as a normal database. The actual backup remains untouched and Rubrik will manage the change tracking for the Live Mount. This does mean that if a Live Mount is discarded, any changes or work done against that database will be lost.

The process for creating live mount is as follows:
1. Create SMB3 share on the Rubrik device
1. Present the database files from a Rubrik snapshot to a SQL Server instance via the SMB3 share
3.  Apply any transaction log backups needed to restore it to the selected point in time.

You can validate/demonstrate the Live Mount by running a query against sys.master_files:
```sql
--show file locations
select db_name(database_id) as DBName
    ,name
    ,physical_name
    ,size/128.0
from
    sys.master_files
where
    db_name(database_id) in ('<Database Name>')
 
 
--You can also use this (H/T Shane Allen)
SELECT
    db.name AS DBName
    ,type_desc AS FileType
    ,Physical_Name AS Location
    ,size/128.0
FROM
    sys.master_files mf
    INNER JOIN sys.databases db ON db.database_id = mf.database_id
```

There are several use cases for Live Mounts, including:

* Object/granular recovery: If the client wants to recover only a portion of data in a database (such as a table or set of rows), they can attach a Live Mount and copy the data from there to the physical database without having to execute a full restore of the database.
* Offline DBCC/consistency checks: Consistency checks can be invasive and affect the overall performance of a database. For larger databases, many shops will restore a copy of the database to another location and run the consistency check against the copy. Live Mounts can be used for this purpose, with some specific caveats that are described below.
* Test/Dev: Live Mounts can be created and hosted to test and development instances. This is a good way to provide clients with a copy of production data without allocating additional storage. Creation of the mounts can be driven by automated scripting and integrated into test workflows for validating releases.
