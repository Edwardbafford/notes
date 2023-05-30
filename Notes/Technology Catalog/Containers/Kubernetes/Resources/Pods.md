
Pod contains one or more containers running on a single host

Usually one main container with a potential supporting container

Get pod data
`kubectl get pod`

# Running

Imperative
`kubectl run NAME --image=IMAGE`

Declarative
`kubectl apply -f FILE.yaml`

Declarative uses JSON/YAML files called resources that can be stored in source control.

Always the better option!

## Format

- spec - specifications for the resource
	- containers - list of containers
		- image - container image
		- imagePullPolicy - when to try and pull the image form the registry: Always, IfNotPresent, Never
		- name - container name
		- resources - computer resource limits and initial requests
		- volumeMounts - volumes to be mounted on container, references the volume name along with any other relevant information
		- env - define environment variables
	- volumes - volumes defined for the pod, comes with a name and type
	- restartPolicy - when to restart a pod: Always, OnFailure, Never

## Probes

All can be defined within the resource file for a container

**Startup Probe** - asks if the container has started and blocks all other probes until this is true

**Readiness Probe** - asks if the container is ready to serve requests

**Liveness Probe** - asks whether the container is healthy, which can trigger a restart from kubernetes


# Troubleshooting

Use port forwarding to access a pod locally, through kubectl
`kubectl port-forward NAME LOCAL_PORT:CONTAINER_PORT`

View container logs
`kubectl logs NAME -c CONTAINER_NAME`

Execute one command within the container
`kubectl exec NAME -- COMMAND`

Execute interactive commands
`kubectl exec -it NAME -- /bin/bash`


# Patterns

## InitContainers

Run before the main container is started and are used to initialize your main container's environment.

Should only be used as a last resort.

## Ambassador Pattern

Use a second container to act as a proxy.

Allows for main containers to be treated normally by developers.

## Sidecar Pattern

Create additional helper containers that provide enhanced functionality
- logging
- monitoring
- configuration requests

## Adapter Pattern

Add a second container to help translate an application aspect into a needed format
- logging
- requests