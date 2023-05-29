Used to run multiple replicas of a [[Pods|Pod]] for horizontal scaling

ReplicaSets are outdated and should only be used through [[Deployment]] resources

## Format

Under spec
- `replicas` - number of replicase of the Pod
- `selector` - how ReplicaSet maps to Pod
	- `matchLabels` - select Pod by label
- `template` - optional section to define a Pod within the ReplicaSet (usually a good idea)
