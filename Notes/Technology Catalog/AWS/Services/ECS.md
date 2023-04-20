
Container management service, alternative to [[Kubernetes]]

Define ECS tasks and launch them on clusters

Launch types
- EC2 - provision EC2 instances to run containers
- Fargate - serverless

Task roles can be assigned to tasks to grant permissions

Integrations
- [[ELB]] - load balancing
- [[EFS]] - mount for storage

Scaling
- Target - scale to maintain metric value
- Step - take action based on alarm 
- Scheduled - take action based on time

