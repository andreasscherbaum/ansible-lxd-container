# ansible-lxd

Ansible role for creating LXD containers

## Main usage

This is primarily my own set of instructions how to create a new container. But feel free to look around ...

## Usage

The type of operating system (and the source of the image) is specified in _defaults/main.yml_, in _lxc_container_os_ and _lxc_container_source_.

This can be overrided in your hosts.cfg, see the [http://docs.ansible.com/ansible/latest/playbooks_variables.html#variable-precedence-where-should-i-put-a-variable](Ansible documentation).

The container name is defined in _lxd_name_, and must be unique on the host. The container host is defined in _ansible_host_.

This role will install [https://www.openssh.com/](OpenSSH) in the newly created container, create keys for root, add them to the known hosts lists on the container, and add the IPv4 address to _/etc/hosts_ on the container host. In short: everything is ready that you can type in "ssh <container>" on the host. Also Python version 2 is installed, in order to manage the container using Ansible.

## Resources

A number of resources is set during container creation (not updated later on):

* CPU allowance: _lxd_cpu_allowance_
* CPU priority: _lxd_cpu_priority_
* Memory limit: _lxd_memory_limit_
* Swap: _lxd_memory_swap_
* Memory limit enforcement: _lxd_memory_enforcement_

Defaults are in _defaults/main.yml_, and can be overridden.

