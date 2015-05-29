Ansible role: ssh
=================

Configure SSH.

Requirements
------------

OS type(s):
- RedHat/CentOS
- Debian/Ubuntu

Role Variables
--------------

TODO.

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: all
      sudo: yes
      gather_facts: yes
      roles:
         - ssh

TODO
----

- Remove workaround for SSH service restart on Ubuntu 14.04 once Ansible update includes fix: https://github.com/ansible/ansible-modules-core/pull/999

License
-------

BSD

Author Information
------------------

https://github.com/craighurley/
