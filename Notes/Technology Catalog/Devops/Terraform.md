Infrastructure as code tool

#### Components
- **Terraform Core** - CLI tool that takes in configuration and state files and uses them to properly apply infrastructure updates
- **Terraform Providers** - plugins used by Terraform to create API calls for different platforms


**Root Module** is a working directory containing `.tf` files which are used to define the Terraform configuration.

All `.tf` files are scanned and combined into a single configuration. Usually split into the following components:
- `main.tf`
- `vars.tf`
- `outputs.tf`
- `backend.tf`

### Providers

Define provider and configure it
```
terraform {
	required providers {
		...
	}
}

provider ... {
	...
}
```


### Variables

Define variables and variable metadata
```
variable "var_name" {
	type = ...
	description = "..."
	sensitive = true/false
	default = ...
}
```

Provide variable values via
- console using `--var` flags
- Variable definitions file with `.tfvars` extensions
- Environment variables `TF_VAR_<VALUE>`


### Resources

Define resources to ensure created by Terraform
```
resource ... {
	...
}
```

Dependencies exist between resources so that the resources can be created in the proper order.

Dependencies can be defined implicitly or explicitly using the `depends_on` attribute.

Export graph to view dependencies: `terraform graph > vm.dot`


### Outputs

Export configuration which can be referenced by other users or modules.
```
output "..." {
	value = RESOURCE.ATTRIBUTE
}
```

Inspect output: `terraform output`


## Commands

`init` - initialize workspace, backend, and download required providers

`plan` - creates an update plan based on the Terraform configuration and current infrastructure state. Save plan with out flag `terraform plan -out output.tfplan`.

`apply` - creates a plan then applies it. Referecne plan file if needed.

`taint` - reference a resource to cause Terraform to re-create the resource next apply.

`destroy` - destroys the infrastructure managed by the state

`fmt` - format configuration files

`validate` - validate configuration files

`show` - output all resources currently being managed


## State

State files are used to track what has been deployed and the resources being managed.

States are stored in backends.

The default backend in the workspace directory 

It's best to use remote backends with the following properties:
- centralized
- encrypted
- automated backups

Configure the backend
```
terraform {
	backend "..." {
		...
	}
}
```

List current resources: `terraform state list`

Remove resource from state: `terraform state rm ...`

Import resource into state: `terraform import <resource> <resource_id>`

A console can be used to interactively investigate the state file: `terraform console`


## Workspaces

Each workspace has a different state file which allows for managing multiple environments.

Create new workspace: `terraform workspace new NAME`

Switch workspace: `terraform workspace select NAME`
