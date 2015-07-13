# personal-vps

[![Build Status](https://travis-ci.org/craighurley/personal-vps.svg?branch=master)](https://travis-ci.org/craighurley/personal-vps)

Create and configure a Virtual Private Server using Ansible.

Ansible will:

- Add users.
- Configure bash.
- Set the locale.
- Tighten SSH security (e.g. allow key auth only).
- Add custom entries to sudo.
- Enable auto security updates.
- Install common applications.
- Configure iptables.
- Enable SELINUX.
- Install NTP.
- Install ZNC.

# Environment

The provisioner passes Ansible a value for `v_environment`; that should be one of the following values:

- `production`
- `staging`
- `development`

This value will effect certain roles, for example, the `bash` role will set the colour of the bash prompt to red, yellow or green depending on the value of `v_environment`.  `v_environment` defaults to `development`.

# Users

See the [users readme](roles/users/) for more information on how to configure users.
