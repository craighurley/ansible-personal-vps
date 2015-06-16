# Ansible role: yum-common

Configure yum: add EPEL, install common packages, enable auto security updates.

# Requirements

OS type(s):
- RedHat/CentOS

# Role Variables

`v_yum_packages`, a list of packages to install.
`v_yum_cron_*`, yum-cron settings.

# Dependencies

None.

# Example Playbook

    - hosts: all
      sudo: yes
      gather_facts: yes
      roles:
         - yum-common

# TODO

None.

# Author Information

https://github.com/craighurley/
