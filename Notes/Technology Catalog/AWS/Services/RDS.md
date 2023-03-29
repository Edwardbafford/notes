
Relational database service

Managed database instances

**Storage Autoscaling** adds storage as needed automatically when storage space is at less than 10% for more than 5 minutes and storage hasn't been added in 6 hours. 

A **maximum storage threshold** should be set for autoscaling.

**RDS Custom** allows for more access but only available for Oracle and SQL Server databases.

Daily backups

Transaction log storage

Manual snapshots for storage, transportation, and restoration



### Read Replicas

Up to 5

Asynchronous replication

New connection string for each replica

Cross region replication is possible but costs extra



### High Availability

Synchronous replication with automatic failover. 

Same connection string.



### Security

[[Security Group|Security groups]] to control access

Username/password

Audit logs



### RDS Proxy

Enable extra convenient features

Pool and share connections

Reduce failover time

Enforce [[IAM]] authentication