# vagrant-vps

Create a Virtualbox VM for development purposes.

Vagrant will:

- Create each of the servers defined in `boxes.yml`.
- Call Ansible to provision the server, with `bootstrap.yml`.  `bootstrap.yml` is used to add specific users and their SSH keys to the server.

# boxes.yml

This file contains a definition of the server(s) that you want to create.

## Required settings

```yaml
- name: vps-centos-1
  description: Personal VPS
  box: puppetlabs/centos-7.0-64-puppet
  box_version: 1.0.1
  cpus: 1
  cpu_execution_cap: 90
  ram: 1024
```

## Optional settings

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

# bootstrap.yml

Ideally you should create development servers so that they resemble the servers that your provider spins up (e.g. DigitalOcean or AWS).  Once your development servers are created, you provision them in the same manner as you would your STAGE or PRODUCTION servers... in my case I use Ansible.

With that in mind, the purpose of `bootstrap.yml` is to simply perform the following:

- Create groups and users, add associated SSH keys.
- Add group `deployment` to sudoers.
- Disable root SSH access.
- Disable SSH password authentication, forcing SSH key based authentication.
- Disable DNS lookups from SSH.
- Allow SSH access to only those users in the group `sshusers`.
