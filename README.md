openscap-sysctl
=========

An Ansible role to apply sysctl settings as successted by openSCAP.

More information regarding the openSCAP can be found [here]([http://static.open-scap.org/)

## Requirements

This role has been tested at a virtualized Ubuntu 20.04 LTS with Ansible Core 2.12.

## Role Variables

A description of the settable variables for this role should go here, including any
variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should
be set via parameters to the role. Any variables that are read from other roles and/or
the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

## Example Playbooks

### Apply ipv4 and ipv6 sysctl parameters

    - hosts: servers
      vars:
        var_apply_openscap_ipv4_sysctl_settings: true
        var_apply_openscap_ipv6_sysctl_settings: true
        var_ipv4_sysctl_state: present
        var_ipv6_sysctl_state: present
      roles:
         - role: openscap-sysctl

### Remove ipv4 settings

    - hosts: servers
      vars:
        var_apply_openscap_ipv4_sysctl_settings: true
        var_apply_openscap_ipv6_sysctl_settings: false
        var_ipv4_sysctl_state: absent
        var_ipv6_sysctl_state: present
      roles:
         - role: openscap-sysctl

## License

MIT

## Author Information
Author: Daniel Kuß
