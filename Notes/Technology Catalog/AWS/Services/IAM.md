Identity and Access Management

A global service for managing AWS users and access

**root account** - user associated with the account, shouldn't be used

**user** - entity to interact with AWS services within an account

**group** - collection of users

**role** - set of permissions that can be assigned to AWS services


## Policy

Policies are created and linked to users, groups, and roles

### Schema

- version
- id
- statement - list of permissions
	- sid - optional id
	- effect - allow or deny
	- principle - acount, role, or user to apply to
	- action
	- resource
	- condition - when to apply


# Passwords

**Password Policy** allows administrators to enforce user's password requirements and behaviors

**Multifactor Authentication** is an option for user authentication


# Auditing

**Credentials Report** - report of user credential statuses

**Access Advisor** - policy update recommendations based on how users have been behaving