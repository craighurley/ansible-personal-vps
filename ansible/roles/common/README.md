Ansible role: common
====================

Configure common items such as groups, users, locale and profile settings.

Requirements
------------

OS is either:
- RedHat/CentOS
- Debian/Ubuntu

Role Variables
--------------

This role requires `v_private_users` and `v_private_user_keys` be configured in `./private/vars/{{ ansible_os_family }}.yml`.  For example:

    ---
    v_private_users:
      -
        id: "johndoe"
        groups: "sshusers,wheel"
      -
        id: "janedoe"
        groups: "sshusers"

    v_private_user_keys:
      -
        id: "johndoe"
        key: "/Users/johndoe/.ssh/id_rsa.pub"


Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      sudo: yes
      gather_facts: yes
      vars_files:
        - "./private/vars/{{ ansible_os_family }}.yml"
      roles:
         - common

TODO
----

- Investigate combining `v_private_users` and `v_private_user_keys` into a single var and handling users with and without keys correctly in `./tasks/auth.yml`

License
-------

BSD

Author Information
------------------

https://github.com/craighurley/
