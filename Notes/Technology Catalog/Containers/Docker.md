## Containers

Software for building Linux containers.
- Namespaces to provide isolation
- cgroups to restrict CPU, memory, and disk consumption

#### Networking

Manipulates host iptables to control how the containers interact with other network entities.

Docker containers each have a unique IP address, allowing them to act as seperate network entities.

## Basics

**Dockerfile** scripts the docker daemon to build an **image**

**Image** is stored in a **repository**

Images are built in **layers** which can be re-used. Start with a base image, add on to the base with dependencies, OS changes, etc. and create an entrypoint which runs on container creation.

Executing an image on the docker daemon creates a **container** which is an instance of the image.

Containers should only ever run one process.

A **multi-stage** build allows you to build an image with one base then switch it to a simpler base for security reasons.