# Ansible role: sudo

Configure sudo.

# Requirements

OS type(s):
- RedHat/CentOS

# Role Variables

None.

# Dependencies

None.

# Example Playbook

    - hosts: all
      sudo: yes
      gather_facts: yes
      roles:
         - sudo

# TODO

None.

# Author Information

https://github.com/craighurley/
