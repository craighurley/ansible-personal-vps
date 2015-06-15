Ansible role: bash
==================

Configure bash for all users.

Requirements
------------

OS type(s):
- RedHat/CentOS

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
         - bash

TODO
----

- Add var to determine colour of prompt (green/dev, yellow/test, red/prod)

License
-------

BSD

Author Information
------------------

https://github.com/craighurley/
