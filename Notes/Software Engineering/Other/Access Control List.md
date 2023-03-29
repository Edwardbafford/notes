List of user with permissions given to an object - user, object, permission

Has issues scaling as the number of users and objects grow.

Groups can help scaling issues - user/group, object, permission

### **Implementation**

- Store ACL in a database
- Update ACLs as necessary
- Enforce ACLs using request filters