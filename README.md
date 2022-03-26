openscap-sysctl
=========

An Ansible role to apply sysctl settings as successted by openSCAP.

More information regarding the openSCAP can be found [here]([http://static.open-scap.org/)

## Requirements

This role has been tested at a virtualized Ubuntu 20.04 LTS with Ansible Core 2.12.

## Role Variables

This role comes with a preset of variables which by default are configured to apply the
openSCAP rules related to the sysctl settings for
* IPv4
* IPv6

The role has 6 variables which can be used to configure the general role behaviour. This
vairables are stored at `defaults/main/generall.yml`:
* (bool) `var_apply_openscap_ipv4_sysctl_settings` and
  `var_apply_openscap_ipv6_sysctl_settings`, which are used to specify the sysctl settings
  to be applied
* (string) `var_ipv4_sysctl_state` and `var_ipv6_sysctl_state`, which are used to specify
  the state of the configured sysctl parameter
* (string) `var_ipv4_sysctl_settings_file` and `var_ipv6_sysctl_settings_file`, which
  specify the filename to store the settings in

The variables which contain the value to be set are stored inside the file
`default/main/sysctl_ipv4_default_settings` and `default/main/sysctl_ipv6_default_settings`.

The full list of the available variables:

    # Disable Accepting ICMP Redirects for All IPv4 Interfaces
    var_net_ipv4_conf_all_accept_redirects

    # Disable Kernel Parameter for Accepting ICMP Redirects by Default on IPv4 Interfaces
    var_net_ipv4_conf_default_accept_redirects

    # Disable Kernel Parameter for Accepting Source-Routed Packets on all IPv4 Interfaces
    var_net_ipv4_conf_all_accept_source_route

    # Disable Kernel Parameter for Accepting Source-Routed Packets on IPv4 Interfaces by
    # Default
    var_net_ipv4_conf_default_accept_source_route

    # Enable Kernel Parameter to Log Martian Packets on all IPv4 Interfaces
    var_net_ipv4_conf_all_log_martians

    # Enable Kernel Paremeter to Log Martian Packets on all IPv4 Interfaces by Default
    var_net_ipv4_conf_default_log_martians

    # Enable Kernel Parameter to Use Reverse Path Filtering on all IPv4 Interfaces
    var_net_ipv4_conf_default_rp_filter

    # Disable Kernel Parameter for Accepting Secure ICMP Redirects on all IPv4 Interfaces
    var_net_ipv4_conf_all_secure_redirects

    # Configure Kernel Parameter for Accepting Secure Redirects By Default
    var_net_ipv4_conf_default_secure_redirects

    # Enable Kernel Parameter to Ignore ICMP Broadcast Echo Requests on IPv4 Interfaces
    var_net_ipv4_icmp_echo_ignore_broadcasts

    # Enable Kernel Parameter to Ignore Bogus ICMP Error Responses on IPv4 Interfaces
    var_net_ipv4_icmp_ignore_bogus_error_responses

    # Enable Kernel Parameter to Use TCP Syncookies on IPv4 Interfaces
    var_net_ipv4_tcp_syncookies

    # Disable Kernel Parameter for Sending ICMP Redirects on all IPv4 Interfaces
    var_net_ipv4_conf_default_send_redirects

    # Disable Kernel Parameter for IP Forwarding on IPv4 Interfaces
    var_net_ipv4_ip_forward

    # Configure Accepting Router Advertisements on All IPv6 Interfaces
    var_net_ipv6_conf_all_accept_ra

    # Disable Accepting ICMP Redirects for All IPv6 Interfaces
    var_net_ipv6_conf_all_accept_redirects

    # Disable Kernel Parameter for Accepting Source-Routed Packets on all IPv6 Interfaces
    var_net_ipv6_conf_all_accept_source_route

    # Disable Kernel Parameter for IPv6 Forwarding
    var_net_ipv6_conf_all_forwarding

    # Disable Accepting Router Advertisements on all IPv6 Interfaces by Default
    var_net_ipv6_conf_default_accept_ra

    # Disable Kernel Parameter for Accepting ICMP Redirects by Default on IPv6 Interfaces
    var_net_ipv6_conf_default_accept_redirects

    # Disable Kernel Parameter for Accepting Source-Routed Packets on IPv6 Interfaces by
    # Default
    var_net_ipv6_conf_default_accept_source_route

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
