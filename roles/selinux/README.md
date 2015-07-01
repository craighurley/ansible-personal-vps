# Ansible role: selinux

Enable and apply various settings to selinux.

# Requirements

OS type(s):
- RedHat/CentOS

# Role Variables

None.

# Dependencies

- Server restart: adding an additional port to the type ssh_port_t cannot be done until after selinux is enabled and the server restarted.  It's safe to re-run the tasks in this role after the restart to make this change.

    ansible-playbook playboook.yml -i inventory.file --tags="selinux"

# Example Playbook

    - hosts: all
      sudo: yes
      gather_facts: yes
      roles:
         - selinux

# TODO

None.

# Author Information

https://github.com/craighurley/
