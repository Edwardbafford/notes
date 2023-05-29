Resource to create persistent storage that can be mapped to [[Volumes|volumes]] and accessed by [[Pods|pods]]

Static Provisioning - admin manually creates the resource

Dynamic Provisioning - define [[StorageClass]] resource within Cloud Platform that will automatically provision new persistent volume resources as needed

## Format

Under spec
- `capacity`
	- `storage`
- `accessModes` - how pods are able to concurrently access the volume `ReadWriteOnce`, `ReadOnlyMany`, `ReadWriteMany`