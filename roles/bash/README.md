# Ansible role: bash

Configure bash for all users.

# Requirements

OS type(s):
- RedHat/CentOS

# Role Variables

Set the colour of the bash prompt to red, yellow or green with `v_environment`:
- production = red
- staging = yellow
- development = green (default)

# Dependencies

None.

# Example Playbook

    - hosts: all
      sudo: yes
      gather_facts: yes
      roles:
         - bash

# TODO

None.

# Author Information

https://github.com/craighurley/
