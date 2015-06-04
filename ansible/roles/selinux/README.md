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

None.

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
