
Elastic Block Store

Network drive that can be attached to [[EC2]] instances

Scoped by AZ

Limited to one [[EC2]] instance at a time

Delete on termination of [[EC2]] instance
- default true for root volume
- default false otherwise

Create snapshot to store and transport between AZ's

Snapshots can be encrypted



# Types


### General Purpose SSD
- gp2 - size and performance are linked
- gp3 - size and performance are independent


### Provisioned IOPS SSD

Better performance than general purpose.

Newer versions have better performance options.

- io1
- io2
- io2 block express


### Hard Disk Drives

Different technology - HDD vs SSD

Generally worse performance

- sc1
- st1