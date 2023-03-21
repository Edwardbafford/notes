Management software designed for Linux container based applications.

Designed to allow for high availability and scalability.

## **Configuration**

K8s cluster is run on a set of nodes, where each node is a machine or VM.

Updates are pushed to K8s cluster via YAML files, usually through a command line tool.

K8s must have access to a Linux container service in order to create the containers needed.

K8s must also have access to all container image repositories in order to download container images needed by the system.

## **Pod**

Pods are deployed within the cluster and managed by K8s.

Pods consist of one or more Linux containers.

Depending on the configuration K8s will monitor pods and scale/restart them as needed.

## **Deployment**

Configuration for deploying pods.

-   Containers to use
-   # of replicas
-   Security config

## **Service**

Service objects can be as an abstraction of a collection of pods to represent a stable API.

-   Maps to a deployment
-   Creates a consistent DNS based on service name
-   Define port

**ClusterIP** type creates service internally

**NodePort** exposes service externally on the given port for each node

## **Ingress Controller**

External endpoint, acting as an [[API gateway]].

Needs cert for external facing TLS. Can use Cert-Manager tool for this.

## **Network Policy**

Configuration that restricts communication between pods.

Define incoming traffic, **ingress** and outgoing traffic, **egress**.

Map policy to pods.

## Secrets

Pass into Kubernetes cluser through the command line or files. Files are more secure.

- Generic Secret - key value pair
- TLS Secret - certificate and private key
- Docker Registry Secret - docker registry access

## **Other**

Creating a **namespace** creates isolation between components of a cluster