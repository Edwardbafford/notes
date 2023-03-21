## **Images**

Start containers as non-root user

Set container file systems to read only

Use minimal images

Set Memory and CPU limits

Sign and validate containers during deployment

## **Kubernetes**

Internal K8s communication should use TLS. This can be implemented using a [[Service Mesh|service mesh]] which will create certificate authorities and cert rotations.

Create a network policy to limit service interactions to only necessary ones.

Use secret objects for managing secrets.