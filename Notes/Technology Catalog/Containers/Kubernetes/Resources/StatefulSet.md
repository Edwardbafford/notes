
A resource similar to a [[Deployment]] that manages [[Pods]] in a stateful way.

Pods are linked to a [[Volumes|volume]] and if the Pod needs to be recreated the Pod will be assigned to the same volume.

1. A headless service must be created as well. Within the service file set `spec.clusterIP: None`
2. Create StatefulSet resource
	- Map to headless service `spec.serviceName: SERVICE_NAME`
	- Map to volume `spec.volumeClaimTemplates`
		- Already created volume or [[StorageClass]]
