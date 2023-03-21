
# **Identity Based Access Control**

What can you do based on who you are

**Users** are authenticated

**Groups** are a collection of users

**Roles** are a collection of permissions

## **Approaches**

-   [[Access Control List||ACL]]
-   [[Role Based Access Control|RBAC]]
-   [[Attribute Based Access Control|ABAC]]

# **Capability Based Access Control**

A **capability** is a reference which identifies a resource and a set of permissions.

An example is a password reset link.

The reference is usually represented as a token embedded in a URI. The same token security applied to [[Authorization|authorization tokens]] should be applied here.

Capabilities allow for very specific scopes to be defined for least privilege to be enforced.

Often a good idea to link a capability with a user or set of users to limit damage if the capability is leaked.

[[Macaroons]] are an extension of capabilities.