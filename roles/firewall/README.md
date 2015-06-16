# Ansible role: firewall

Disable firewalld, install and enable iptables, then configure iptables rules.

# Requirements

OS type(s):
- RedHat/CentOS

# Role Variables

`v_firewall_inbound_ports`, a list of ports to open.

    ---
    v_firewall_inbound_ports:
      -
        port: "53"
        protocol: "udp"
      -
        port: "443"
        protocol: "tcp"

Note: Allowing tcp/22 is hardcoded in the template.

# Dependencies

None.

# Example Playbook

    - hosts: all
      sudo: yes
      gather_facts: yes
      roles:
         - firewall

# TODO

None.

# Author Information

https://github.com/craighurley/
