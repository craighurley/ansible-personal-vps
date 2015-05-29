Ansible role: common
====================

Configure common items such as groups, users, locale and profile settings.

Requirements
------------

OS type(s):
- RedHat/CentOS
- Debian/Ubuntu

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
         - common

TODO
----

None.

License
-------

BSD

Author Information
------------------

https://github.com/craighurley/
