Configuration as code tool

Ansible is installed an run from a control node. The control node will need to have SSH access to all managed nodes that it will be configuring.

Features
- Declarative
- Idempotent
- Defined through YAML code
- Executes in parallel for higher performance


## Configuration

Configuration file defines global properties specific to an Ansible instance.

```
[defaults]
inventory = ...
...
```

Configuration file can be found in the following ways:
- `ANSIBLE_CONFIG` environment variable which points to the configuration file
- `ansible.cfg` in the current directory
- `ansible.cfg` in the home directory of the user
- `ansible.cfg` in the `/etc/ansible` directory


## Inventory

Inventory is defined through an inventory file which groups managed nodes into roles.

There is also an `all:var` section which can be used to define variables that will be applied to all roles.

```
[role1]
node1
node2
[role2]
node3
node4
[all:var]
...
```

See inventory structure: `ansible-inventory --list -y`

See hosts: `ansible --list hosts all/ROLE`

Ping hosts: `ansible all/ROLE -m ping`


## Modules

Modules are code packages used by Ansible to execute tasks.


## Tasks

Tasks are commands sent to Ansible, usually referencing a module.

Execute task: `ansible ... all/role`

Execute task with module: `ansible -m module_name ... all/role`


## Playbooks

Playbooks consist of one or more plays. 

A play references a set of hosts and a set of sequenced tasks.

```
- hosts: ...
  become: True/False (use root user)
  tasks:
    - name: ...
      action: module command
	  notify:
	    - handler name
  handlers:
	- name: handler name
	  service: module command
```

Tasks can also notify handlers in order to execute extra logic if necessary. 

Playbooks can reference and import other playbooks
`- import playbook: ....yaml`

Check playbook syntax: `ansible-playbook playbook.yaml --syntax-check`

Apply playbook: `ansible-playbook playbook.yaml`

Playbooks are executed in three steps
- Gathering facts - checking hosts and gathering information
- Run tasks - executing tasks in order as defined by the playbook
- Play recap - provide recap information


## Variables

Inject variables into Playbooks with the following format: `" {{ var_name }} "`

Variables can be set:
- `vars` section of a playbook
- inventory file
- roles
	- within role directory structure
	- within playbooks linking to a role
- command line
- return value of a task using `register` keyword with a playbook

Simple variable hold a single value to be referenced

List variables contain a list of values
```
var:
  - v1
  - v2
  - v3
```
List variable values can be referenced as `" {{ var[0] }} "`

Dictionary variables contain a set of key value pairs
```
var
  - k1: v1
  - k2: v2
```
Dictionary variables can be referenced as `" {{ var[k1] }} "`


## Roles

Roles are defined within a directory structure and referenced by playbooks.

They are used to help create loosely coupled configuration logic between system components.

Here is the directory structure
```
roles
	role_name
		tasks
		handlers
		library
		files
		templates
		vars
		defaults
		meta
```

- tasks - task yaml files defined through a `main.yaml`
- handlers - handlers defined through a `main.yaml`
- library - external modules to include for the role
- file - external files needed for the configuration
- templates - external files that can be injected with variables
- vars - variables for the role defined through a `main.yaml`
- defaults - variables for the role that may change at runtime, defined through a `main.yaml`
- meta - metadata and dependencies for the role defined through a `main.yaml`
