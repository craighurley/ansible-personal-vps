# personal-vps

[![Build Status](https://travis-ci.org/craighurley/vagrant-vps.svg?branch=master)](https://travis-ci.org/craighurley/vagrant-vps)

Create and configure a Virtual Private Server using Ansible and Vagrant.

For local development, Vagrant will:
- Download a box/image.
- Create a VM.
- _TODO: Run a basic Ansible provisioning playbook._
- Add hostname to the local hosts file.

For all other environments use Ansible to:
- Create VM(s).
- Configure the VM(s).

# Boxes

`boxes.yml` contains a definition of the box(es) that you want to create.

## Required settings

```yaml
- name: vps-centos
  description: Personal VPS
  box: puppetlabs/centos-7.0-64-puppet
  cpus: 1
  cpu_execution_cap: 90
  ram: 1024
```

## Optional settings

### Box version

You can tie the box to a specific version by setting `box_version`:

```yaml
- name: vps-centos
  box: puppetlabs/centos-7.0-64-puppet
  box_version: 1.0.1
```

### Network

In order to add a bridged network, you can simply add the name of the interface you wish to bridge to, e.g.

```yaml
public_network:
  bridge: "en0: Wi-Fi (AirPort)"
```

The above example relies on DHCP to allocate an IP for the bridged interface, but if you want to define a static IP:

```yaml
public_network:
  bridge: "en0: Wi-Fi (AirPort)"
  ip: 192.168.2.101
```

# TODO

- Add basic provisioning (create user and add an SSH key)
- Add digital ocean provider.
- Assign boxes to groups in inventory file.
