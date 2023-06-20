
Deploy-time security mechanism that ensures only trusted binary files are deployed within an environment.

### Kubernetes

For [[Kubernetes|K8s]], a ruleset is defined to only allow images signed by an attestation authority to be deployed.

This policy is enforced through an admission controller.