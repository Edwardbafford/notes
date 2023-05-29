Expose workloads internally and externally

Services can be dynamically accessed via Pod environment variables 

`SERVICE_NAME_SERVICE_PORT`
`SERVICE_NAME_SERVICE_HOST`

## Format 

Under spec
- `ports`
	- `port` - port to expose
	- `protocol` - TCP or UDP
	- `targetPort` - port linking to container
- `selector` - how to select [[Pods|Pod]] to expose
- `type` - service type

# Types

The service types layer on top of each other.

## ClusterIP

The lowest layer of services and the default.

Expose pods within the K8s cluster only.

## NodePort

Expose Pods to a port on each node, runs on top of ClusterIP.

Because exposing ports on individual nodes is awkward, it's never really used on its own.

`type: NodePort`

## LoadBalancer

Expose the pods through a single endpoint which load balances across nodes.

`type: LoadBalancer`

Can only be used within supported cloud platforms as K8s needs to call the Cloud Platform to create this external endpoint.

Will create a NodePort service behind it.