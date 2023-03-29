Authorization decisions are made dynamically based on attributes of the request.

Often useful to layer on top of a [[Role Based Access Control|RBAC]] system.

## **Attributes**

- user
- resource
- action
- environment

## **Outcome**

- Allow
- Deny

# **Implementations**

Policy as code using a ABAC framework.

**Policy Agents** can plug into your systems.

**Distributed Policy Enforcement**: Use external server with API which is used by other services to enforce policy.