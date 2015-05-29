Ansible role: yum
=================

Configure yum: add EPEL, configure auto security updates.

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
         - yum

TODO
----

- Add yum cache update
- Switch from lineinfile to template when modifying yum-cron.conf

License
-------

BSD

Author Information
------------------

https://github.com/craighurley/
