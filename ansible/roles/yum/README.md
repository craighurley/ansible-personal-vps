Ansible role: yum
=================

Configure yum: add EPEL, configure auto security updates.

Requirements
------------

OS is either:
- RedHat/CentOS

Role Variables
--------------

TODO.

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

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
