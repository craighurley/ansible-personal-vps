# vagrant-ansible-vps

[![Build Status](https://travis-ci.org/craighurley/vagrant-ansible-vps.svg?branch=master)](https://travis-ci.org/craighurley/vagrant-ansible-vps)

Create and configure a Virtual Private Server.

Ansible will:

- Add users.
- Tighten SSH security (e.g. allow key auth only).
- Configure iptables.
- Enable SELINUX.
- Enable auto security updates.
- Install common applications.
- Install ZNC in a docker container.
- Configure bash.

# boxes.yml
This file contains a definition of the box(es) that you want to create.

## Required settings
    - name: vps-centos-1
      description: Personal VPS
      box: puppetlabs/centos-7.0-64-puppet
      box_version: 1.0.1
      ansible_playbook: vps.yml
      ansible_log_level: v
      cpus: 1
      cpu_execution_cap: 90
      ram: 1024

## Optional settings:
### Network
In order to add a bridged network, you can simply add the name of the interface you wish to bridge to, e.g.

      public_network:
        bridge: "en0: Wi-Fi (AirPort)"

The above example relies on DHCP to allocate an IP for the bridged interfcae, but if you want to define a static IP:

      public_network:
        bridge: "en0: Wi-Fi (AirPort)"
        ip: 192.168.2.101

### Environment
By default, the provisioner passes ansible a value for `v_environment`.  That can be `Nil` or it can be one of the following values:

- production
- staging
- development

This value will effect certain roles, for example, the `bash` role will set the colour of the bash prompt to red, yellow or green depending on the value of `v_environment`.

# Users

See the [users readme](roles/users/) for more information on how to configure users.

# TODO

- Add ZNC role.
