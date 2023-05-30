A VPC is a defined IP range network that you can control and work with.

All AWS Accounts have a default VPC which is public

VPCs are regionally scoped

[[EC2]] instances map to the default VPC unless otherwise defined

VPC routing is controlled through **Routing Tables**

VPC can enable IPv6


## Subnet

A subset of the VPC IP range

The first 4 and last 1 IP address of a subnet is taken by AWS

- Public subnet - available through the internet
- Private subnet - not available through the internet


## Internet Gateway

Allow resources in VPC to connect to the internet

one-to-one relationship with VPC


## NAT Instance

Network address translation

Allows connection from a public subnet to a private subnet

Created within a public subnet

Can connect an internet gateway to the NAT instance to allow public access

Old and outdated!


## NAT Gateway

AWS managed NAT

AZ scoped


## Egress-only Internet Gateway

NAT Gateway for IPv6

Outbound connections only, no inbound connections


## NACL

Netword access control list

Firewall for subnet

Default is allow all

Rules
- define rule priority
- define ALLOW or DENY
- first rule to match is executed


## VPC Peering

Allow two VPC to communicate privately

IP ranges can't overlap


## VPC Endpoints

Connect to AWS services internally

- Gateway - [[S3]] and [[DynamoDB]]
- Interface - anything else


## Traffic Mirroring

Capture and inspect VPC traffice

Route to security application


