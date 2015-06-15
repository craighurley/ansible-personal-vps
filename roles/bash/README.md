Ansible role: bash
==================

Configure bash for all users.

Requirements
------------

OS type(s):
- RedHat/CentOS

Role Variables
--------------

- Set the colour of the bash prompt to red, yellow or green with `v_bash_prompt_colour`:
-- 1 is red, for PROD
-- 3 is yellow, for TEST
-- 2 is green, for DEV

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

Improve setting colour of bash prompt.

License
-------

BSD

Author Information
------------------

https://github.com/craighurley/
