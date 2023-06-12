
Tool for creating VM snapshot artifacts that can easily be deployed.

Called **machine images**

Packer file defines the process for creating the machine image.

- Variables for runtime configuration
- Builders - define how to create the base VM
- Provisioners - define how to configure the VM

1. Build VM from base image
2. Run a "provisioner" to configure the VM
3. Turn off the VM
4. Take a snapshot
5. Save the snapshotas a disk image
6. Save the image to a repository

`packer build <PACKER_FILE>`

