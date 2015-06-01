Ansible role: users
===================

Add and configure groups and users.

Requirements
------------

OS type(s):
- RedHat/CentOS

Role Variables
--------------

This role requires `v_private_users` to be configured in `./private/vars/{{ ansible_os_family }}.yml`.  For example:

    ---
    v_private_users:
      -
        id: "johndoe"
        groups: "sshusers,wheel"
        key: "/Users/johndoe/.ssh/id_rsa.pub"
      -
        id: "janedoe"
        groups: "wheel"


Dependencies
------------

None.

Example Playbook
----------------

    - hosts: all
      sudo: yes
      gather_facts: yes
      vars_files:
        - "./private/vars/{{ ansible_os_family }}.yml"
      roles:
         - users

TODO
----

None.

License
-------

BSD

Author Information
------------------

https://github.com/craighurley/
