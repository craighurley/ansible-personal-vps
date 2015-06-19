# Ansible role: users

Add and configure groups and users.

# Requirements

OS type(s):
- RedHat/CentOS

# Role Variables

This role requires `v_private_users` to be configured in `./private/vars/users.yml`.  For example:

    v_private_users:
      - username: "johndoe"
        groups: "sshusers,wheel"
        key: "/Users/johndoe/.ssh/id_rsa.pub"
        password: "$6$rounds=100000$rNIt2ifVCefWLf1m$V65ESpHfpf4yQx9oUwDdR2tBM9TKg2ZaRZ50v.a8gnT3GEuivFZL4Sijexel5bRgZxbi4uuzX6ErYgr/ZlC8r0"
      - username: "janedoe"
        groups: "wheel"
        password: "$6$rounds=100000$pxo3TtGDUjvgQ0gh$yeYhyLHtHO7zR2U9GUWMoHaByvQCj410diEofYr/OsHgnEBJ3XATSGghTK41YdKnhroiEsCEsTZxuTPWxOX/h/"

You can also delete users by adding a list of usernames to `v_private_users_delete` in `./private/vars/users.yml`.  For example:

    v_private_users_delete:
      - username: "johnsmith"
      - username: "janesmith"

Note: the deleted users home directory is not removed, so numeric user ids are not accidentally reused.

To create the password value, the mkpasswd utility that is available on most Linux systems is a great option:

        mkpasswd --method=SHA-512

If this utility is not installed on your system (e.g. you are using OS X) then you can still easily generate these passwords using Python. First, ensure that the Passlib password hashing library is installed.

        pip install passlib

Once the library is ready, SHA512 password values can then be generated as follows:
        python -c "from passlib.hash import sha512_crypt; import getpass; print sha512_crypt.encrypt(getpass.getpass())"

Source: http://docs.ansible.com/faq.html#how-do-i-generate-crypted-passwords-for-the-user-module

# Dependencies

See the [bash readme](../bash/) for more information on how to configure users.

# Example Playbook

    - hosts: all
      sudo: yes
      gather_facts: yes
      vars_files:
        - "./private/vars/users.yml"
      roles:
         - users

# TODO

None.

# Author Information

https://github.com/craighurley/
