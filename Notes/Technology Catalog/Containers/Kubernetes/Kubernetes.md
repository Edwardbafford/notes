
Container orchestration system

# Architecture

Consists of a cluster of nodes - control pane and worker nodes

**Control pane** is a collection of services that manage the cluster

**Worker nodes** provide the compute power for running the applications deployed to K8s

## Components

### Control Pane

**API Server** - all internal and external communicate runs through the API server component

**Controller manager** - takes actions based on the current state and the desired state

**Node controller** - manages nodes and pods

**Replication controller** - manages the container replicas

**Endpoints controller** - provides service endpoints to containers

**Service account** and **Token controllers** - create accounts and tokens for each namespace

**Cloud controller manager** - optional controller that interacts with cloud provider APIs

**etcd** - key value stored for K8s metadata and configuration

**Scheduler** - schedules containers in a worker node

### Worker Node

**kubelet** - interacts with underlying container runtime

**kube-proxy** - sets up network components for containers to interact with


# Commands

Get resource
`kubectl get RESOURCE_KIND RESOURCE_NAME`

View kubernetes events related to a resource
`kubectl describe RESOURCE_KIND RESOURCE_NAME`

Delete resource
`kubectl delete RESOURCE_KIND RESOURCE_NAME`

## Format

Create/update resource
`kubectl apply -f FILE.yaml`

- apiVersion - resource version
- kind - kind of resource
- metadata - name and label data for identifying and grouping resources

# Components
- [[Pods]]
- [[Volumes]]
- [[ConfigMaps]]
- [[Secrets]]