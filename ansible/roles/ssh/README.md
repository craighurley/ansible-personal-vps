Ansible role: ssh
=================

Configure SSH.

Requirements
------------

OS is either:
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

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      sudo: yes
      gather_facts: yes
      roles:
         - ssh

TODO
----

- Remove workaround for https://github.com/ansible/ansible-modules-core/pull/999 once Ansible updated includes fix.

License
-------

BSD

Author Information
------------------

https://github.com/craighurley/
