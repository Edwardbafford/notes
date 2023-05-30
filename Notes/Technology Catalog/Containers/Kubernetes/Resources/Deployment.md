Manages [[Pods]] and how they are deployed/replicated

Format is the same as a [[ReplicaSet]]

Deployments usually contain ReplicaSets and Pods within them!

Deploy new version
`kubectl set image deployment/DEPLOYMENT_NAME CONTAINER_NAME=IMAGE:TAG --record`

Record saves it to the deployment history

Check status
`kubectl rollout status deployment DEPLOYMENT_NAME`

Check deployment history
`kubectl rollout history deployment DEPLOYMENT_NAME`

Undo deployment
`kubectl rollout undo deployment DEPLOYMENT_NAME`

## Strategies

Recreate - delete the old pods then create new ones

In format: `spec.strategy.type: Recreate`

Rolling Update - delete old pods while creating new ones

In format:
`spec.strategy.type: RollingUpdate`
	- `maxSurge` - max over replicas
	- `maxUnavailable` - max under replicas