# Azure Roles Collection for Ansible Automation Platform

This repository hosts the `cloud.azure_ops` Ansible Collection.

The collection includes a variety of Ansible roles and playbook to help automate the management of resources on Microsoft Azure.

<!--start requires_ansible-->
## Ansible version compatibility

This collection has been tested against following Ansible versions: **>=2.9.17**.

## Included content

Click on the name of a plugin or module to view that content's documentation:

<!--start collection content-->
### Roles
Name | Description
--- | ---
[cloud.azure_ops.azure_load_balancer_with_public_ip](https://github.com/redhat-cop/cloud.azure_ops/blob/main/roles/azure_load_balancer_with_public_ip/README.md)|A role to manage Azure Load Balancer.
[cloud.azure_ops.azure_manage_postgresql](https://github.com/redhat-cop/cloud.azure_ops/blob/main/roles/azure_manage_postgresql/README.md)|A role to manage Azure PostGreSQL Database.
[cloud.azure_ops.azure_manage_network_interface](https://github.com/redhat-cop/cloud.azure_ops/blob/main/roles/azure_manage_network_interface/README.md)|A role to manage Azure Network Interface.
[cloud.azure_ops.azure_manage_networking_stack](https://github.com/redhat-cop/cloud.azure_ops/blob/main/roles/azure_manage_networking_stack/README.md)|A role to manage Azure Networking Stack.
[cloud.azure_ops.azure_manage_resource_group](https://github.com/redhat-cop/cloud.azure_ops/blob/main/roles/azure_manage_resource_group/README.md)|A role to manage Azure Resource Group.
[cloud.azure_ops.azure_manage_security_group](https://github.com/redhat-cop/cloud.azure_ops/blob/main/roles/azure_manage_security_group/README.md)|A role to manage Azure Security Group.
[cloud.azure_ops.azure_virtual_machine_with_public_ip](https://github.com/redhat-cop/cloud.azure_ops/blob/main/roles/azure_virtual_machine_with_public_ip/README.md)|A role to manage Azure Virtual Machine.


### Playbooks
Name | Description
--- | ---
[cloud.azure_ops.webapp](https://github.com/redhat-cop/cloud.azure_ops/blob/main/playbooks/WEBAPP.md)|A playbook to deploy a web application on azure using virtual machines.
[cloud.azure_ops.webapp_container](https://github.com/redhat-cop/cloud.azure_ops/blob/main/playbooks/WEBAPP_CONTAINER.md)|A playbook to deploy a web application on azure using containers.
[cloud.azure_ops.vmss_migrate](https://github.com/redhat-cop/cloud.azure_ops/blob/main/playbooks/VMSS_MIGRATE.md)|A playbook to migrate virtual machines of a web application from one azure region to another region.
[cloud.azure_ops.validate_deployment](https://github.com/redhat-cop/cloud.azure_ops/blob/main/playbooks/VALIDATE_DEPLOYMENT.md)|A playbook to validate successful deployment of web application URL.
<!--end collection content-->

## Installation and Usage

### Installation
Clone the collection repository.

```shell
  mkdir -p ~/.ansible/collections/ansible_collections/cloud/azure_ops
  cd ~/.ansible/collections/ansible_collections/cloud/azure_ops
  git clone https://github.com/redhat-cop/cloud.azure_ops .
```

### Using this collection

Once installed, you can reference the cloud.azure_ops collection content by its fully qualified collection name (FQCN), for example:

```yaml
  - hosts: all
    tasks:
        - name: Create load balancer
            ansible.builtin.include_role:
                name: cloud.azure_ops.azure_load_balancer_with_public_ip
            vars:
                operation: create
                azure_resource_group: "{{ resource_group }}"
                azure_load_balancer:
                name: "{{ resource_group }}-lb"
```

### See Also

* [Ansible Using collections](https://docs.ansible.com/ansible/latest/user_guide/collections_using.html) for more details.


## Contributing to this collection

We welcome community contributions to this collection. If you find problems, please open an issue or create a PR against this collection repository.

### Testing and Development

The project uses `ansible-lint` and `black`.
Assuming this repository is checked out in the proper structure,
e.g. `collections_root/ansible_collections/cloud/azure_ops/`, run:

```shell
  tox -e linters
```

Sanity and unit tests are run as normal:

```shell
  ansible-test sanity
```

There are also integration tests in the `molecule` directory which are meant to be run against an azure subscription.

```shell
    az login
    molecule test
```

This collection is tested using GitHub Actions. To know more about CI, refer to [CI.md](https://github.com/redhat-cop/cloud.azure_ops/blob/main/CI.md).

## License

GNU General Public License v3.0 or later

See [LICENCE](https://github.com/redhat-cop/cloud.azure_ops/blob/main/LICENSE) to see the full text.
