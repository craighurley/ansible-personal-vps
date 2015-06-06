Ansible role: selinux
======================

Enable and apply various settings to selinux.

Requirements
------------

OS type(s):
- RedHat/CentOS

Role Variables
--------------

None.

Dependencies
------------

- Adding an additional port to the type ssh_port_t cannot be done until after selinux is enabled and the server restarted.

Example Playbook
----------------

    - hosts: all
      sudo: yes
      gather_facts: yes
      roles:
         - selinux

TODO
----

None.

License
-------

BSD

Author Information
------------------

https://github.com/craighurley/
